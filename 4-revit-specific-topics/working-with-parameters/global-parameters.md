---
description: Global parameters are accessible by any element in the model
---

# Global Parameters

#### A New Kind of Parameter

In Revit 2016, a new kind of parameter was introduced to to the application: the [Global Parameter](https://knowledge.autodesk.com/support/revit-products/getting-started/caas/CloudHelp/cloudhelp/2018/ENU/Revit-Model/files/GUID-1AA9B2DC-C08B-458E-BA93-C72C109D61C8-htm.html). These were designed to let the users control a value from a single location, which could be referenced anywhere in the model.

In Revit's API, there are a few classes which relate to this new functionality:

* \*\*\*\*[**GlobalParameterManager Class**](https://apidocs.co/apps/revit/2019/f3af05ec-1f0c-fe86-6708-0a211a40bcda.htm): This is used to access any global parameters in a Revit document.
* \*\*\*\*[**GlobalParameter Class**](https://apidocs.co/apps/revit/2019/b0e53a4a-84ad-abb4-358d-9797870f101b.htm): Objects of this class represent a single global parameter.

#### Accessing Global Parameters

We can retrieve any or all global parameters in a document using the GlobalParameterManager class, like so:

```python
#Boilerplate Code

#To retrieve a list of all global parameters' IDs we can use:
all_global_parameter_ids = GlobalParameterManager.GetAllGlobalParameters()

#We can also retrieve a single global parameter using its name
test_parameter_id = GlobalParameterManager.FindByName("Test")

#Finally, we can get the GlobalParameter object using the Document.GetElement() method:
test_parameter = doc.GetElement(test_parameter_id)
OUT = test_parameter
```

#### Getting and Setting Values

We can retrieve the value from any GlobalParameter object using its GetValue\(\) method, like so:

```python
#Boilerplate Code
test_parameter_id = GlobalParameterManager.FindByName("Test")
test_parameter = doc.GetElement(test_parameter_id)
value = test_parameter.GetValue().Value
```

We can also set the value, using the SetValue\(\) method, although it will need to be [wrapped in a transaction](../working-with-transactions.md), as we're editing the Revit document.

