---
description: >-
  Project information parameters are a bit meta - they're information about the
  document they're a part of.
---

# Project Information Parameters

#### Introduction

Project Information Parameters are a special category of parameters, which are read in the UI via their own special dialog \(_Manage&lt;Settings&lt;Project Information_\). They are created like any other parameter, in the Project Parameters dialog, but they are assigned to the 'Project Information' category.

Typically, this is used to store information such as:

* The name of your organisation
* The name of the project
* The project code/number

#### Retrieving Project Information Parameters

We first need to retrieve the [ProjectInfo](https://apidocs.co/apps/revit/2019/e90b12f3-9bf4-f536-3556-c9944cbf9f38.htm) object using a [FilteredElementCollector](../fetching-revit-elements.md), like so:

```python
#Boilerplate Code
project_info = FilteredElementCollector(doc).OfCategory(BuiltInCategory.OST_ProjectInformation).ToElements()
#This returns a list of parameters, but it will only
#ever be 1 item long, so we need to get the first element
#by its index using [0]
project_info = project_info[0]
#Now we can access its ParameterSet, its set of parameters
project_info_parameters = project_info.Parameters
OUT = project_info_parameters
```

In the example above, we output the Parameter objects from the Python node, however, we can just as easily iterate through each parameter, outputting its name and value.

```python
#Boilerplate Code
project_info = FilteredElementCollector(doc).OfCategory(BuiltInCategory.OST_ProjectInformation).ToElements()[0]
project_info_parameters = project_info.Parameters

output_list = []
for parameter in project_info_parameters:
    output_list.append([parameter.Definition.Name, parameter.AsString()])
OUT = output_list
```

Note: The example above will output all values as strings, regardless of their original datatype. It's possible to avoid this by querying the Parameter's StorageType property and using the appropriate conversion method for each type.

