2017 Apple established the WebGPU Community Group inside the W3C to standardize a new 3D graphics API. This new Web API is implementable on top of Metal, Direct3D, and Vulkan. All of the major browser vendors are participating and contributing to the standardization effort.

Shaders are programs that take advantage of the specialized architecture of GPUs.

Apps designed for Metal use the Metal Shading Language, apps designed for Direct3D 12 use HLSL, and apps designed for Vulkan use SPIR-V or GLSL. WebGPU is designed to work on top of Metal, Direct3D 12, and Vulkan, so the shaders need to be able to be represented in a form that each of those APIs can accept.

WebGPU platform consists of the following layers:
1. User agent implementing the specification.
2. Operating system with low-level native API drivers for this device.
3. Actual CPU and GPU hardware.

Entry point to WebGPU.
```rust
Instance {
    pub fn new(backends: BackendBit) -> Self;
    pub fn enumerate_adapters(&self, backends: BackendBit) -> impl Iterator<Item = Adapter>;
    pub fn request_adapter(&self, options: &RequestAdapterOptions<'_>) -> impl Future<Output = Option<Adapter>> + Send;
    pub unsafe fn create_surface<W: HasRawWindowHandle>(&self, window: &W) -> Surface;
}
```

An adapter represents an implementation of WebGPU on the system.
An adapter may be a physical display adapter (GPU), but it could also be a software renderer. Applications can hold onto multiple adapters at once.
```rust
Adapter {
    fn get_info(&self) -> AdapterInfo;
    fn features(&self) -> Features;
    fn limits(&self) -> Limits;
    fn request_device(&self, desc: &DeviceDescriptor, trace_path: Option<&Path>) -> Impl Future<Output = Result<(Device, Queue), RequestDeviceError>> + Send
}
```
A device is the logical instantiation of an adapter, through which internal objects are created.
```rust
Device {
    pub fn poll(&self, maintain: Maintain);
    pub fn features(&self) -> Features;
    pub fn limits(&self) -> Limits;

    pub fn create_buffer(&self, desc: &BufferDescriptor<'_>) -> Buffer;
    pub fn create_texture(&self, desc: &TextureDescriptor<'_>) -> Texture;
    pub fn create_sampler(&self, desc: &SamplerDescriptor<'_>) -> Sampler;

    pub fn create_bind_group(&self, desc: &BindGroupDescriptor<'_>) -> BindGroup;
    pub fn create_bind_group_layout(&self, desc: &BindGroupLayoutDescriptor<'_>) -> BindGroupLayout;
    pub fn create_pipeline_layout(&self, desc: &PipelineLayoutDescriptor<'_>) -> PipelineLayout;

    pub fn create_shader_module(&self, source: ShaderModuleSource<'_>) -> ShaderModule;
    pub fn create_render_pipeline(&self, desc: &RenderPipelineDescriptor<'_>) -> RenderPipeline;
    pub fn create_compute_pipeline(&self, desc: &ComputePipelineDescriptor<'_>) -> ComputePipeline;
    pub fn create_swap_chain(&self, surface: &Surface, desc: &SwapChainDescriptor) -> SwapChain;

    pub fn create_command_encoder(&self, desc: &CommandEncoderDescriptor<'_>) -> CommandEncoder;
    pub fn create_render_bundle_encoder(&self, desc: &RenderBundleEncoderDescriptor<'_>) -> RenderBundleEncoder<'_>;
}
```

A Buffer represents a block of memory that can be used in GPU operations. Data is stored in linear layout, meaning that each byte of the allocation can be addressed by its offset from the start of the Buffer, subject to alignment restrictions depending on the operation.

A BindGroup defines a set of resources to be bound together in a group and how the resources are used in shader stages.

A PipelineLayout defines the mapping between resources of all BindGroup objects set up during command encoding in setBindGroup, and the shaders of the pipeline.

#### Separation of concerns

In WebGL, a single context object is responsible for everything, and it contains a lot of associated state.
In contrast, WebGPU separates these into multiple different contexts:
- GPUDevice creates resources, such as textures and buffers.
- GPUCommandEncoder allows encoding individual commands, including render and compute passes.
- Once done, it turns into GPUCommandBuffer object, which can be submitted to a GPUQueue for execution on the GPU.
- We can present the result of rendering to the HTML canvas. Or multiple canvases. Or no canvas at all – using a purely computational workflow.

Overall, this separation will allow for complex applications on the web to stream data in one or more workers and create any associated GPU resources for it on the fly. Meanwhile, the same application could be recording work on multiple workers, and eventually submit it all together to GPUQueue. This matches multi-threading scenarios of native graphics-intensive applications and allows for high utilization of multi-core processors.

### Pipeline state

In WebGL, the user would create a shader program at program initialization. Later when the user attempts to use this shader program, the driver takes into consideration all the other states currently set, and may need to internally recompile the shader program. If the driver does recompile the shader program, this could introduce CPU stalls.

In contrast, WebGPU has the concept of a pipeline state object (namely, GPURenderPipeline and GPUComputePipeline). A pipeline state object is a combination of various states that the user creates in advance on the device – just like in native APIs. The user provides all this state upfront, which allows the browsers and hardware drivers to avoid extra work (such as shader recompilation) when it’s used later in GPU operations.

From the developer perspective, it’s easier to manage these coarse state objects as well. They don’t have to think as much about which of the fine-grained states to change, and which ones to preserve.

The pipeline state includes:
- Shaders
- Layouts of vertex buffers and attributes
- Layouts of bind groups
- Blending, depth, and stencil states
- Formats of the output render targets

### Binding model
A third difference between WebGPU and WebGL is the binding model. The WebGPU binding model allows resources to be grouped together into a BindGroup object. Then we bind GPUBindGroups during command recording in order to use the resources within shaders.

By creating these bind groups upfront, the graphics driver can perform any necessary preparations in advance. This allows the browser to change resource bindings much faster between draw calls.

Most importantly, the user has to describe the layout of resource bindings ahead of time, baking it into a GPUBindGroupLayout object. Both pipeline states and concrete bind groups know about the bind group layout as well. This knowledge serves as a contract between the shader and the API. It allows the browser or the driver to lay out resources in a way that allows faster binding.