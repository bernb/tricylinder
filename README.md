# tricylinder

## Summary
Single function to create a triangulated cylinder. This function mimics Matlab's [cylinder](https://www.mathworks.com/help/matlab/ref/cylinder.html) behavior, but returns a [triangulation](https://www.mathworks.com/help/matlab/ref/triangulation.html) object instead of x-, y- and z-coordinates.

## Syntax
TR = tricylinder

TR = tricylinder(r)

TR = tricylinder(r,n)

tricylinder(___)

tricylinder(ax,___)

## Description
TR = tricylinder returns the triangulation object of a cylinder without drawing it. The cylinder has a radius of 1 and 20 equaly spaced points around its circumference. The bases are parallel to the xy-plane. To draw the cylinder, pass TR to the trisurf or trumesh function.

---

TR = tricylinder(r) returns the triangulation object of a cylinder with the specified profile curve r, and 20 equally spaced points around its circumference. The function treats each element in r as a radius at equally spaced heights along the unit height of the cylinder.

---

TR = tricylinder(r,n) returns the triangulation object of a cylinder with the specified profile curve r, and n equally spaced points around its circumference.

---

tricylinder(___) plots the cylinder without returning the coordinates. Use this syntax with any of the input arguments in previous syntaxes.

---

tricylinder(ax,___) plots into the axes specified by ax instead of the current axes. Specify the axes as the first input argument.

## Background
Existing solutions for triangulations are limited to surfaces that can be defined by a function `f(x,y)=z` and thus not allow cylinders. Solutions based on interpolation have slow performance and do not result in a homogeneous mesh. Just like [cylinder](https://www.mathworks.com/help/matlab/ref/cylinder.html), tricylinder allows the simple construction of a cylinder defined by an vector `r` containing the profile curve and a positive whole number `n` that defines the number of points around the cylinder circumfence.
