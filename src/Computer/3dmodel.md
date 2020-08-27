# 3D Model

### glTF (Graphics Library Transmission Format or GL Transmission Format)

https://www.khronos.org/gltf/

- 2015-10-19 glTF 1.0 specification was announced
- 2017-06-05 glTF 2.0 was published at the Web3D 2017 Conference
- royalty-free file format for 3D scenes and models using the JSON standard
- API-neutral runtime asset delivery format developed by the Khronos Group

In comparison to the older OBJ format, which supports only vertices, normals, texture coordinates, and basic materials, glTF provides a more powerful set of features. In addition to all of the above, glTF offers:

- Hierarchical objects
- Scene information (light sources, cameras)
- Skeletal structure and animation
- More robust materials and shaders

Advantages of glTF 2.0 format
- Combine all geometries, meshes, vertices, material textures and shading in a single file, reducing network overhead for downloading multiple asset files
- Supports Draco mesh compression algorithm by Google for smaller file size, quicker download
- Binary format supports direct loading into GPU buffer
- Support Physically Based Rendering (PBR) for realistic shading and light (metallic roughness and specular-glossiness material model)
- Animation support, key frames and skin inverse bind matrices
- Support morph targets for facial animations

For simple models with no animation, OBJ is nevertheless a common and reliable choice.

In comparison to COLLADA or FBX, the supported features are very similar. However, because glTF focuses on providing a “transmission format” rather than an editor format, it is more interoperable with web technologies. glTF is the "JPEG of 3D".

Geometry in a glTF model may be compressed using the Draco library. For models containing primarily geometry, with simple untextured materials or vertex colors, compression can often reduce file size by 90–95%.

![](images/2017-gltf-20-launch-2_1.jpg)

GLB file format is a binary form of glTF that includes textures instead of referencing them as external images.

The glTF JSON may contain scenes (with an optional default scene). Each scene can contain an array of indices of nodes.
Each node may refer to a mesh or a camera, using indices that point into the meshes and cameras arrays.
Each of the nodes can contain an array of indices of its children.
A node may contain a local transform. The global transform of a node is given by the product of all local transforms on the path from the root to the respective node.

A transform can be given as a column-major matrix array, or with separate translation, rotation and scale properties, where the rotation is given as a quaternion.

The meshes may contain multiple mesh primitives.
Each mesh primitive has a rendering mode, which is a constant indicating whether it should be rendered as POINTS, LINES, or TRIANGLES.
The primitive also refers to indices and the attributes of the vertices, using the indices of the accessors for this data.
The material that should be used for rendering is also given, by the index of the material.

The buffers contain the data that is used for the geometry of 3D models, animations, and skinning.
The bufferViews add structural information to this data.
The accessors define the exact type and layout of the data.

mesh primitive "mode":

    - 0: "POINTS"
    - 1: "LINES"
    - 2: "LINE_LOOP"
    - 3: "LINE_STRIP"
    - 4: "TRIANGLES"
    - 5: "TRIANGLE_STRIP"
    - 6: "TRIANGLE_FAN"

accessor data item "type":

    - "SCALAR"
    - "VEC2"
    - "VEC3"
    - "VEC4"
    - "MAT2"
    - "MAT3"
    - "MAT4"
    
"componentType": 

    - 5120: "BYTE"
    - 5121: "UNSIGNED_BYTE"
    - 5122: "SHORT"
    - 5123: "UNSIGNED_SHORT"
    - 5125: "UNSIGNED_INT"
    - 5126: "FLOAT"

## UV mapping

UV mapping is the 3D modeling process of projecting a 2D image to a 3D model's surface for texture mapping. The letters "U" and "V" denote the axes of the 2D texture because "X", "Y", and "Z" are already used to denote the axes of the 3D object in model space,

UV texturing permits polygons that make up a 3D object to be painted with color (and other surface attributes) from an ordinary image. The image is called a UV texture map.

## UV unwrapping

UV coordinates (also known as texture coordinates) can be generated for each vertex in the mesh. The operation of generating these UV maps is also called “unwrap”, since it is as if the mesh were unfolded onto a 2D plane.

A UV map can either be generated automatically by the software application, made manually by the artist, or some combination of both. Often a UV map will be generated, and then the artist will adjust and optimize it to minimize seams and overlaps. If the model is symmetric, the artist might overlap opposite triangles to allow painting both sides simultaneously.

The UV mapping process at its simplest requires three steps: unwrapping the mesh, creating the texture, and applying the texture to a respective face of the mesh.

UV mapping may use repeating textures, or an injective 'unique' mapping as a prerequisite for baking.

If a 3D object has a UV map, then, in addition to the 3D coordinates X, Y, and Z, each point on the object will have corresponding U and V coordinates.

