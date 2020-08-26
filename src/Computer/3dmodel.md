# 3D Model

### glTF (Graphics Library Transmission Format or GL Transmission Format)

https://www.khronos.org/gltf/

- 2015-10-19 glTF 1.0 specification was announced
- 2017-06-05 glTF 2.0 was published at the Web3D 2017 Conference
- royalty-free file format for 3D scenes and models using the JSON standard
- API-neutral runtime asset delivery format developed by the Khronos Group

![](images/2017-gltf-20-launch-2_1.jpg)

GLB file format is a binary form of glTF that includes textures instead of referencing them as external images.

In comparison to the older OBJ format, which supports only vertices, normals, texture coordinates, and basic materials, glTF provides a more powerful set of features. In addition to all of the above, glTF offers:

- Hierarchical objects
- Scene information (light sources, cameras)
- Skeletal structure and animation
- More robust materials and shaders

For simple models with no animation, OBJ is nevertheless a common and reliable choice.

In comparison to COLLADA or FBX, the supported features are very similar. However, because glTF focuses on providing a “transmission format” rather than an editor format, it is more interoperable with web technologies. glTF is the "JPEG of 3D".

Geometry in a glTF model may be compressed using the Draco library. For models containing primarily geometry, with simple untextured materials or vertex colors, compression can often reduce file size by 90–95%.
