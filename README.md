# tricylinder

## Summary
Single function to create a triangulated cylinder. This function mimics Matlab's [cylinder](https://www.mathworks.com/help/matlab/ref/cylinder.html) behavior, but returns a [triangulation](https://www.mathworks.com/help/matlab/ref/triangulation.html) object instead of x-, y- and z-coordinates.

## Syntax
TR = tricylinder

TR = tricylinder(r)

TR = tricylinder(r,n)

[TR, T, x, y, z] = tricylinder(r,n)

tricylinder(___)

tricylinder(ax,___)

## Description
TR = tricylinder returns the triangulation object of a cylinder without drawing it. The cylinder has a radius of 1 and 20 equaly spaced points around its circumference. The bases are parallel to the xy-plane. To draw the cylinder, pass TR to the trisurf or trumesh function.

---

TR = tricylinder(r) returns the triangulation object of a cylinder with the specified profile curve r, and 20 equally spaced points around its circumference. The function treats each element in r as a radius at equally spaced heights along the unit height of the cylinder.

---

TR = tricylinder(r,n) returns the triangulation object of a cylinder with the specified profile curve r, and n equally spaced points around its circumference.

---

[TR, T, x, y, z] = tricylinder(___)  returns the triangulation object together

---

tricylinder(___) plots the cylinder without returning the coordinates. Use this syntax with any of the input arguments in previous syntaxes.

---

tricylinder(ax,___) plots into the axes specified by ax instead of the current axes. Specify the axes as the first input argument.

## Background
Existing solutions for triangulations are limited to surfaces that can be defined by a function `f(x,y)=z` and thus not allow cylinders. Solutions based on interpolation have slow performance and do not result in a homogeneous mesh. Just like [cylinder](https://www.mathworks.com/help/matlab/ref/cylinder.html), tricylinder allows the simple construction of a cylinder defined by an vector `r` containing the profile curve and a positive whole number `n` that defines the number of points around the cylinder circumfence.

## Examples
### Display Unit Cylinder
Create and plot a cylinder with a radius equal to 1. 
```
cylinder
```

### Specify Cylinder Radius and Height
Specify the radius of a cylinder by including the input r. Then, specify the height of the cylinder by modifying the z-coordinates of the returned triangulation object.
```
r = 4;
[~, T, x, y, z] = tricylinder(r);
```
Specify a height of 20 by modifying the z-coordinates. Plot the cylinder.
```
h = 20;
z = z*h;
TR = triangulation(T, x, y, z);
trisurf(TR)

### Display Multiple Cylinders at Different Locations
Create a cylinder and use the returned coordinates to plot multiple cylinders in different locations.

Create a cylinder defined by the profile function 2 + cos(t).
```
t = 0:pi/10:2*pi;
r = 2 + cos(t);
[TR, T, x, y, z] = tricylinder(r);
```
Plot two more cylinders on top of the first cylinder.
hold on
z = z+1;
TR2 = triangulation(T, x, y, z);
z = z+1;
TR3 = triangulation(T, x, y, z);
trisurf(TR2);
trisurf(TR3);
```
