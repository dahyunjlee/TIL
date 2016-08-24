#Geometry

###Points and Vertices

A *point* is simply a point in space as defined by four numbers (X, Y, Z, W).

A *vertex* is a reference to a point. Primitives use vertices to reference points. For example, the corners of a polygon, the center of a sphere, or a control vertex of a spline curve.

Primitives can share points, while vertices are unique to a primitive.

*source: [houdini documentation] (http://www.sidefx.com/docs/houdini/model/points)*

###Primitives
*Primitives* refer to a unit of geometry, lower-level than an object but above points. Similar to faces in other cad systems.

* Packed primitives
    - Represent lightweight reference to geometry stored somewhere else
    - Useful for copying/instancing

* Quadratic primitive types
    - Represent geometry mathematically rather than as polygonal surfaces
    - ex) Null, circle(point, rotation, radius), sphere/ellipsoid, tube/cone

Polygons and Meshes
* Polygons: shapes constructed from a series of straight edges, which are defined by a series of vertices
* Ideal for dealing with complex typologies that go beyond the four sided nature of meshes and NURBS surfaces
* A *mesh* is a collection of polygons with guaranteed ordering. 
    - much more efficient that the equivalent polygons
    - unlike most regular polygons, can convert it directly to NURBS
    - the Convert surface node can convert mesh primitives to regular polygons when you want a nice layout of polygons in rows and columns


###Attributes
*Attributes* are named values stored on vertices, points, primitives, and objects. ex) point color, position, uv coordinates, spline weight, normal...

Can attach attributes to (in order of precedence):
* Vertex    : vertex of primitives
* Point     : points in space
* Primitive : shapes
* Detail    : entire piece of geometry


