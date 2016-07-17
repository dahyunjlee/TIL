#Raytracing Algorithms
Raytracer found [here](https://github.com/dahyunjlee/raytra).

##Ray-Box Intersections

Check each pair of parallel lines. Find each tfar and tnear value. If the overal tnear is smaller than tfar, the ray intersects the box.

###Pseudocode

set Tnear = - infinity, Tfar = infinity

**For each** pair of planes P associated with X, Y, and Z **do**:
(example using X planes) (d = ray direction, o = ray origin)
**if dx = 0** then the ray is parallel to the X planes, so
if ox is not between the slabs ( ox < xmin or ox > xmax ) 
then return false

**else** if the ray is not parallel to the plane then
compute the intersection distance of the planes
T1 = (xmin - ox) / dx
T2 = (xmax - ox) / dx
If T1 > T2 swap (T1, T2) /* since T1 intersection with near plane */
If T1 > Tnear set Tnear = T1 /* want largest Tnear */
If T2 < Tfar  set Tfar  = T2 /* want smallest Tfar */
If Tnear > Tfar box is missed so return false
If Tfar < 0 box is behind ray return false 

If Box survived all above tests, return true with **intersection point Tnear and exit point Tfar**.

###C++ Code
```cpp
bool BBox::intersect(const Ray &ray, Intersection &it) {
    
    Vector n;
    double d, txmin, txmax, tymin, tymax, tzmin, tzmax, tnear, tfar;

    if (ray.d.x == 0) {
        if (ray.o.x < min.x)
            txmin = txmax = INFINITY;
        else if (ray.o.x > max.x)
            txmin = txmax = -INFINITY;
        else {
            txmin = -INFINITY;
            txmax = INFINITY;
        }
    }
    else {
        d = 1/ray.d.x;  //the sign determines which is the nearer plane
        if (d >= 0) {
            txmin = d*(this->min.x - ray.o.x);
            txmax = d*(this->max.x - ray.o.x);
            tnear = txmin;
            n = Vector (-1, 0, 0);
        }
        else {
            txmin = d*(this->max.x - ray.o.x);
            txmax = d*(this->min.x - ray.o.x);
            tnear = txmin;
            n = Vector (1, 0, 0);
        }
    }

    if (ray.d.y == 0) {
        if (ray.o.y < min.y) 
            tymin = tymax = INFINITY;
        else if (ray.o.y > max.y)
            tymin = tymax = -INFINITY;
        else {
            tymin = -INFINITY;
            tymax = INFINITY;
        }
    }
    else {
        d = 1/ray.d.y;
        if (d >= 0) {
            tymin = d*(this->min.y - ray.o.y);
            tymax = d*(this->max.y - ray.o.y);
            if (tymin > tnear) {
                tnear = tymin;
                n = Vector (0, -1, 0);
            }
        }
        else {
            tymin = d*(this->max.y - ray.o.y);
            tymax = d*(this->max.x - ray.o.y);
            if (tymin > tnear) {
                tnear = tymin;
                n = Vector (0, 1, 0);
            }
        }
    }

    if (ray.d.z == 0) {
        if (ray.o.z < min.z)
            tzmin = tzmax = INFINITY;
        else if (ray.o.z > max.z)
            tzmin = tzmax = -INFINITY;
        else {
            tzin = -INFINITY;
            tzmax = INFINITY;
        }
    }
    else {
        d = 1/ray.d.z;
        if (d >= 0) {
            tzmin = d*(this->min.z - ray.o.z);
            tzmax = d*(this->max.z - ray.o.z);
            if (tzmin > tnear) {
                tnear = tzmin;
                n = Vector (0, 0, -1);
            }
        }
        else {
            tzmin = d*(this->max.z - ray.o.z);
            tzmax = d*(this->min.z - ray.o.z);
            if (tzmin > tnear) {
                tnear = tzmin;
                n = Vector (0, 0, 1);
            }
        }
    }

    tfar = fmin (txmax, fmin (tymax, tzmax));

    if (tnear > tfar) return false;
    if (tfar < 0) return false;

    it.t = tnear;
    it.p = ray.o + ray.d * tnear;
    it.n = n;

    return true;
}
```
