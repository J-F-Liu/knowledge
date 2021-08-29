建模思路：点连成线，线连成圈，圈界定面，面连成壳，壳连成体，体组成模型。
快捷方法：挤出/扫射、镜像、修饰（比如边缘圆角）、增加厚度

A subset S of the plane is called convex if and only if for any pair of points p,q ∈ S the line segment pq is completely contained in S.
The convex hull of a set S is the smallest convex set that contains S. It is the intersection of all convex sets that contain S.
It is the unique convex polygon whose vertices are points from P and that contains all points of P.

### Polygon

We say a polygon is in standard form if all its vertices are distinct and no three consecutive vertices are collinear.
We define a simple polygon as a polygon in which no nonconsecutive edges share a point.
If a polygon is simple, as you traverse the edges the interior bounded region is always to one side.
Two vertices of a simple polygon are said to be mutually visible if the straight line segment connecting them does not intersect the exterior of the polygon.
We define a triangulation of a simple polygon P as a partitioning of the interior of P into triangular regions constructed by joining mutually visible vertices of P by nonintersecting straight line segments.
Any triangulation of the polygon must use n − 3 diagonals and contains n − 2 triangles.
Computing the triangulation of a polygon is a fundamental algorithm in computational geometry.

A convex vertex is one for which the interior angle is smaller than 180 degrees.
A concave vertex is one for which the interior angle formed by the two edges sharing it is larger than 180 degrees.

We define an ear of P as a convex vertex whose neighbor vertices are mutually visible.
A principal vertex of a simple polygon is called a mouth if the diagonal of neighbor vertices lies outside the boundary of the polygon.

To mesh a polygon with high-quality triangles, a mesh generator usually introduces additional vertices that are not vertices of the polygon.
The added vertices are often called Steiner points, and the mesh is called a Steiner triangulation of the polygon.

### Delaunay triangulation

For a set P of points in the plane the Delaunay triangulation is a triangulation DT(P) such that no point in P is inside the circumcircle of any triangle in DT(P).
Delaunay triangulations maximize the minimum angle of all the angles of the triangles in the triangulation, not the edge-length of the triangles; they tend to avoid skinny triangles.
By considering circumscribed spheres, the notion of Delaunay triangulation extends to three and higher dimensions.

Every finite set of points in the plane has a Delaunay triangulation.
The Delaunay triangulation of point set S is unique if and only if no four points in S lie on a common circle.
The Delaunay triangulation optimizes several geometric criteria when compared with all other triangulations of the same point set.

A constrained triangulation is a triangulation that enforces the presence of specified edges—for example, the boundary of a nonconvex object.

A Steiner Delaunay triangulation of polygon, also known as a conforming Delaunay triangulation, is a Steiner triangulation in which every simplex is Delaunay.

Delaunay mesh generator place additional vertices, making incremental insertion.

Delaunay refinement algorithms construct a Delaunay triangulation and refine it by inserting new vertices, chosen to eliminate skinny or oversized elements, while always maintaining the Delaunay property of the mesh.

Triangulated Irregular Network
TINs can have a higher resolution in areas where a surface is highly variable or where more detail is desired and a lower resolution in areas that are less variable.
TIN models are less widely available than raster surface models and are more time consuming to construct and process.

### Mesh

Mesh geometry is basically a collection of points in 3D space, also called vertices, and a number of faces connecting those points together.

Using quads is often preferred during modeling since they can be more easily enhanced and smoothed than triangles.
For rendering and game engines though, working with triangles is often easier since every shape can be rendered very efficiently using triangles.

### Triangle Mesh

A triangle mesh is a type of polygon mesh in computer graphics. It comprises a set of triangles that are connected by their common edges or corners.
There are two primary ways of passing a triangle mesh to the graphics hardware, triangle strips and index arrays.

A triangle strip is a series of connected triangles from the triangle mesh, sharing vertices, allowing for more efficient memory usage for computer graphics.
Triangle strips are a memory optimization, not a speed optimization.

The reason why a triangle list can be equaly or more efficient than a triangle strip is indices. Indices let the hardware transform and cache vertices in a very previsible fashion, given that you are optimizing your geometry and triangle order correctly.

The simplest and most famous way to smooth an interior vertex is to move it to the centroid of the vertices that adjoin it.
This method, which dates back at least to Kamel and Eisenstein in 1970, is called Laplacian smoothing because of its interpretation as a Laplacian finite difference operator.

### B-spline curve

Insert a new knot t into the knot vector without changing the shape of the B-spline curve, p-1 control points of the original control polyline are removed and replaced with p new control points.

[NURBS and CAD: 30 Years Together](http://isicad.net/articles.php?article_num=14940)

### Boundary Representation (B-rep or BREP)

A solid is represented as a collection of connected surface elements, which define the boundary between interior and exterior points.

### Function Representation (FRep or F-Rep)

The points with $f(x_{1},x_{2},...,x_{n})\geq 0$ belong to the object, and the points with ${\displaystyle f(x_{1},x_{2},...,x_{n})<0}$ are outside of the object. The point set with ${\displaystyle f(x_{1},x_{2},...,x_{n})=0}$ is called an isosurface.

Many operations such as set-theoretic, blending, offsetting, projection, non-linear deformations, metamorphosis, sweeping, hypertexturing, and others, have been formulated for this representation in such a manner that they yield continuous real-valued functions as output, thus guaranteeing the closure property of the representation.

## Articles

- 1992 Triangulation of trimmed surfaces in parametric space
  perform the triangulation completely inparametric space, trimmed regions are mapped into parametric space and approximated by 2D polygonal regions,
  then triangulated by a restricted Delaunay triangulation algorithm, generated triangles are subdivided further until each edge of the triangles is smaller
  than the allowed length that results from the surface definition and the specified tolerance.

- 1995 Tessellating trimmed nurbs surfaces, Leslie A Piegl and Arnaud M Richard
  Obtain a polygonal approximation of trimming curves in parameter space, triangulate the trimmed region, map the triangles onto the surface and build a 3D triangular mesh.
  Given a trimming edge, find a point to form a valid triangle for which the angle at this point is the largest and the sides of the triangle do not intersect any of the trimming edges.
  The number of triangles computed in parameter space depends on the bounds of the second derivatives.

- 1998 Geometry-based triangulation of trimmed NURBS surfaces, Les A Piegl and Wayne Tillert
  subdivide the surface using its control net and store subdivision rectangles in the parameter domain;
  merge trimming polygons and subdivision rectangles to yield new closed domain polygons; triangulate domain polygons;

- 2005 GPU-based trimming and tessellation of NURBS and T-Spline surfaces
  convert trimming curves into a approximate polygon, generate trim-texture by spanning a triangle fan from the first vertex of each trimming loop and consider the even-odd-rule.
  approximates each NURBS or T-Spline surface with a coarse hierarchy of rational bi-cubic Bezier patches, the patch is sampled using a regular grid of sufficient resolution.

- 2007 Direct Evaluation of NURBS Curves and Surfaces on the GPU
  evaluates the NURBS surface point coordinates directly, without resorting to piecewise bezier approximations;
  knot array texture is generated on the CPU, computing spline basis function on the GPU.
  trim-texture is generated by evaluating and rendering the trim curves in the 2D parametric domain.

- 2009 Direct trimming of NURBS surfaces on the GPU
  use a ray-based point-in-closed curve method (”even-odd-rule”) to determine if a particular point should remain or has to be trimmed;
  split the trimming curves into monotonic segments, which are guaranteed to have at most one intersection with a ray parallel to one of the parameter domain axes.
  perform the bisection method only for points contained in the bounding boxes of the curve segments with a hierarchical acceleration structure.

- 2012 An Efficient Trim Structure for Rendering Large B-Rep Models
  approximate input trimming curves with connected 2D quadratic Bézier curves, and stored in a quadtree built over the parametric space of each basis surface;
  a multiresolution lookup reducing screen flicker and accelerate point classification on distant and close objects.

-
