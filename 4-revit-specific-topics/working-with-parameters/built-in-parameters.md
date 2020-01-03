---
description: These are hard-baked into the Revit software - we can't define or delete them
---

# Built-In Parameters

#### Introduction

Built-in parameters \(written BuiltInParameter\) are a special kind of parameter and the only kind of Revit parameter which cannot be modified in any way \(even by us programmers\).

These are used to refer to many hard-coded parts of the application that we can't change. For instance, family instances will have a few parameters we can't remove, no matter how we try. This could be a 'Mark' or an 'Offset from Level' value.

#### The BuiltInParameter Enumeration

Since the [list of BuiltInParameters](https://apidocs.co/apps/revit/2019/fb011c91-be7e-f737-28c7-3f1e1917a0e0.htm) is hard-coded, it makes sense to store these in an enumeration. The names of each parameter may differ slightly from how they appear in the user-interface, so each BuiltInParameter is stated alongside its UI-name. Each parameter has an underscore-separated name written in all-capitals.

For instance, say we wanted to read the sill height from a window we've placed \(as in this example from the excellent [spiderinnet blog](https://spiderinnet.typepad.com/blog/2011/04/parameter-of-revit-api-1-builtinparameter.html)\), we could use:

```python
#Boilerplate Code
my_window = UnwrapElement(IN[0])
sill_height = my_window.get_Parameter(BuiltInParameter.INSTANCE_SILL_HEIGHT_PARAM).AsDouble()
OUT = sill_height
```

While there is no foolproof, easy way to identify the BuiltInParameter you're looking for, the following steps may help:

* Find the name the parameter is referred to in the UI and use a CTRL+F search in the [BuiltInParameter Enumeration](https://apidocs.co/apps/revit/2019/fb011c91-be7e-f737-28c7-3f1e1917a0e0.htm) page of APIDocs.co.
* Run a quick Google search to see if others have already asked the same question.
* Use the excellent [RevitLookup add-in](https://apidocs.co/apps/revit/2019/fb011c91-be7e-f737-28c7-3f1e1917a0e0.htm) for Revit. Harry Mattison of [BoostYourBIM](https://boostyourbim.wordpress.com/) has created installers for each version, making installation quick and easy.

