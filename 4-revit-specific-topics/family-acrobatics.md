---
description: >-
  Wouldn't it be so easy if we could just use a single line of code to move
  between FamilyInstance, FamilyType and Family objects?
---

# 4.13 Family Acrobatics

**Going Between FamilyInstance, FamilyType and Family**

When working with scripts, I often need to go between accessing a FamilyInstance’s parameters, its Type Parameters and sometimes its Family parameters. The Revit API provides methods to move between these in a straightforward manner.

Generally speaking, a FamilyInstance is a Revit family you can click on and inspect in a Revit view. This is a fairly straightforward type of content and it’s correspondingly straightforward to access its parameters.

We can write a simple function to help speed up the process.  


