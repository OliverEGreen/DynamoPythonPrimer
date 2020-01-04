---
description: Family -> FamilyType -> FamilyInstance -> FamilyType -> Family
---

# 4.13 Family Acrobatics

**Going Between FamilyInstance, FamilyType and Family**

The Revit application uses a hard-coded hierarchy between [Family](https://www.revitapidocs.com/2015/f51d019d-6ff3-692b-d1d2-b497cab564de.htm),[ FamilyType](https://www.revitapidocs.com/2015/7f15b213-c99b-db59-3622-3280757b82d9.htm) and [FamilyInstance](https://www.revitapidocs.com/2015/0d2231f8-91e6-794f-92ae-16aad8014b27.htm) objects. A family may contain many family types, a family type may be placed many times.

When working with scripts, I often need to go between accessing a FamilyInstance’s parameters, its Type Parameters and sometimes Family. The Revit API provides methods to move between these in a straightforward manner.

#### Moving Upstream from FamilyInstance -&gt; FamilyType -&gt; Family

Each FamilyInstance will derive from a single FamilyType. Likewise, each FamilyType will be defined by a single Family in the document. We can move upstream from FamilyInstance to Family like so:

```python
#Boilerplate Code

family_instance = UnwrapElement(IN[0])
family_type_id = family_instance.GetTypeId()
family_type = doc.GetElement(family_type_id)
family = family_type.Family
OUT = family_instance, family_type, family
```

#### Moving Downstream from Family -&gt; FamilyTypes -&gt; FamilyInstances

This way is more complicated; there is a many-to-one relationship between a Family object and its many potential FamilyType objects. Likewise, there could be many placed FamilyInstances of any FamilyType. To get all family\_types of a family, we could use:

```python
#Boilerplate Code

family = UnwrapElement(IN[0])
family_type_ids = family.GetFamilySymbolIds()
family_types = [doc.GetElement(id) for id in family_type_ids]
OUT = family_types
```

Finding all FamilyInstance objects of a given Type is less straightforward - we'll first need to create a [FamilyInstanceFilter](https://www.revitapidocs.com/2015/ec0bdad7-e213-f22a-94ef-bc0fd96ac641.htm) using the Id of the required FamilyType. 

```python
#Boilerplate Code

family = UnwrapElement(IN[0])
family_type_ids = family.GetFamilySymbolIds()

family_instances = []

for family_type_id in family_type_ids:
	family_instance_filter = FamilyInstanceFilter(doc, family_type_id)
	elements = FilteredElementCollector(doc).WherePasses(family_instance_filter).ToElements()
	family_instances.append(elements)

OUT = family_instances
```

On Line 9 above, we create the FamilyInstanceFilter, which takes our [document](doc-uidoc-app-uiapp.md) and the FamilyType's Id as arguments. We can then pass this in as a modifier to the [FilteredElementCollector](fetching-revit-elements.md) on Line 10.

