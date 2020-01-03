---
description: >-
  Accessing parameters is one of the fundamental skills you’ll need to get up
  and running with the Revit API. However, the Revit parameter system itself is
  somewhat complex.
---

# 4.7 Working With Parameters

**Working With Parameters**

There are a few different ways to set up parameters in Revit and each of them has a corresponding different way of being accessed.

* Shared parameters \(defined in a .txt file\)
* Project parameters \(defined in a .rvt file\)
* Family parameters \(defined in a .rfa file\)
* BuiltInParameters \(hard-baked into the Revit software itself\)

Shared, Project and Family parameters are known as '**custom parameters**' as users can define them as they wish; we'll look at [BuiltInParameters](built-in-parameters.md) separately. Each kind of custom parameter has a different way of being accessed within a project. 

* Global parameters \(accessible everywhere throughout the file\)
* Family Instance and Family Type parameters \(accessible via a family type or a family instance\)
* Project Information parameters \(accessed via the project information dialog\)
* Group parameters \(accessed through a group definition or a group instance\)

Finally, custom parameters can be made category-specific, so they might only be valid for Revit categories \(e.g. a parameter that only applies to sheets\).

#### Identifying Which Is Which

To get started with accessing a parameter using code, we’ll first need to identify which sort of parameter you’re wanting to access. Follow these steps to figure out what you're working with:

1. Does the parameter appear in the Properties Window when you click on a Revit family instance? This means it is an [instance parameter](instance-parameters.md).
2. If not visible in the Properties Window, does it appear when you click on the family and open the 'Edit Type' window? If so, then it's a [type parameter](instance-parameters.md).
3. Does the parameter appear in the Manage &gt; Global Parameters dialog? If so, it's a global parameter and there are [special ways to access this](global-parameters.md). 
4. If the parameters appears in the Manage &gt; Project Information parameter, there's a [special way to access this](project-information-parameters.md), too.
5. Does the parameter appear in the Properties Window when you click on a model or detail group? This means it is a [group instance parameter](group-parameters.md).
6. If not visible in the Properties Window, does it appear when you click on the group and open the 'Edit Type' window? Then it's a [group type parameter](group-parameters.md).

