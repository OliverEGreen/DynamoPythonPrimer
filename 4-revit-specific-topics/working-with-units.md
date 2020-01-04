---
description: 'Feet, Inches, Meters and Millimetres'
---

# 4.11 Working With Units

#### How Revit Measures Lengths

When retrieving any length value using Revit's API, it will automatically be returned in decimal feet \(for example, 6 inches = 0.5 Feet\). Displaying lengths in any commonly-used format will require special conversion methods. In the example below, we feed a 5,000mm line into the Python Script node:

```python
#Boilerplate Code

detail_line = UnwrapElement(IN[0])
decimal_feet_length = detail_line.GeometryCurve.Length
OUT = decimal_feet_length
```

The above code returns a value of 16.404, which is the same length but measured decimal feet.

#### Converting Between Units

Decimal feet isn't very useful to anyone so you'll want to convert to something more helpful. To make this conversion, we'll want to use Revit's [UnitUtils](https://apidocs.co/apps/revit/2019/128dd879-fea8-5d7b-1eb2-d64f87753990.htm) class. Furthermore, we'll be restricted to choosing value types from Revit's [DisplayUnitType](https://apidocs.co/apps/revit/2019/7d3d3306-a4c2-c577-0aeb-cca42d6cfd2f.htm) enumeration. Let's see this in action:

```python
#Boilerplate Code

detail_line = UnwrapElement(IN[0])
decimal_feet_length = detail_line.GeometryCurve.Length
metric_length = UnitUtils.Convert(decimal_feet_length, DisplayUnitType.DUT_DECIMAL_FEET, DisplayUnitType.DUT_MILLIMETERS)
OUT = metric_length
```

#### Bonus: Converting Rotations

Sometimes when passing an angle value in to the Revit API, it needs to be converted from degrees to radians first. This can also be done using UnitUtils.Convert\(\), like so:

```python
#Boilerplate Code

angle = 90.0
radians_equivalent = UnitUtils.Convert(angle, DisplayUnitType.DUT_DECIMAL_DEGREES, DisplayUnitType.DUT_RADIANS)
OUT = radians_equivalent
```

