# OpenBox Location Conditions

Added new conditions to the [If action's](http://openbox.org/wiki/Help:Actions#If) query:
  - `min_x`
  - `max_x`
  - `min_y`
  - `max_y`
  - `min_width`
  - `max_width`
  - `min_height`
  - `max_height`

which compare the supplied integer value against the active window's in relative numbers to the active screen.

This is especially usefull when moving windows around with custom arrow binds like in Windows.

That can be seen [here](./example_config/rc.xml.md)

## Simple example

```xml
<action name="If">
  <query target="default">
    <min_x>50<min_x>
  </query>
  <then>
    <action name="Maximize"/>
  </then>
  <else>
    <action name="Iconify"/>
  </else>
</action>
```
