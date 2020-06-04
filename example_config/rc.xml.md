# Example Windows-like keybindings

This makes OpenBox behave almost like Windows

```xml
<keyboard>

  ...

  <!-- Show Desktop -->
  <keybind key="W-d">
    <action name="ToggleShowDesktop"/>
  </keybind>

  <!-- Move the window to the left or to the previous window  -->
  <keybind key="W-Left">
    <action name="If">
      <query target="default">
        <max_x>1</max_x>
        <max_y>1</max_y>
        <max_width>50</max_width>
        <min_height>90</min_height>
      </query>
      <then>
        <action name="MoveResizeTo"><monitor>prev</monitor><x>-0</x><y>0</y><height>100%</height><width>50%</width></action>
      </then>
      <else>
        <action name="UnmaximizeFull"/>
        <action name="MoveResizeTo"><x>0</x><y>0</y><height>100%</height><width>50%</width></action>
      </else>
    </action>
  </keybind>

  <!-- Move the window to the right or to the next window -->
  <keybind key="W-Right">
    <action name="If">
      <query target="default">
        <min_x>40</min_x>
        <max_y>1</max_y>
        <max_width>50</max_width>
        <min_height>90</min_height>
      </query>
      <then>
        <action name="MoveResizeTo"><monitor>next</monitor><x>0</x><y>0</y><height>100%</height><width>50%</width></action>
      </then>
      <else>
        <action name="UnmaximizeFull"/>
        <action name="MoveResizeTo"><x>-0</x><y>0</y><height>100%</height><width>50%</width></action>
      </else>
    </action>
  </keybind>

  <!-- Move the window up or maximize -->
  <keybind key="W-Up">
    <action name="If">
      <query target="default">
        <max_x>1</max_x>
        <max_y>1</max_y>
        <max_width>50</max_width>
        <min_height>60</min_height>
      </query>
      <then>
        <action name="UnmaximizeFull"/>
        <action name="MoveResizeTo"><x>0</x><y>0</y><width>50%</width><height>50%</height></action>
      </then>
      <else>
        <action name="If">
          <query target="default">
            <max_x>1</max_x>
            <max_y>1</max_y>
            <min_width>99</min_width>
          </query>
          <then>
            <action name="Maximize"/>
          </then>
          <else>
            <action name="If">
              <query target="default">
                <min_x>40</min_x>
                <max_y>1</max_y>
                <max_width>50</max_width>
                <min_height>60</min_height>
              </query>
              <then>
                <action name="UnmaximizeFull"/>
                <action name="MoveResizeTo"><x>-0</x><y>0</y><width>50%</width><height>50%</height></action>
              </then>
              <else>
                <action name="UnmaximizeFull"/>
                <action name="MoveResizeTo"><x>0</x><y>0</y><width>100%</width><height>50%</height></action>
              </else>
            </action>
          </else>
        </action>
      </else>
    </action>
  </keybind>

  <!-- Move the window down or minimize -->
  <keybind key="W-Down">
    <action name="If">
      <query target="default">
        <max_x>1</max_x>
        <max_y>1</max_y>
        <max_width>50</max_width>
      </query>
      <then>
        <action name="UnmaximizeFull"/>
        <action name="MoveResizeTo"><x>0</x><y>-0</y><width>50%</width><height>50%</height></action>
      </then>
      <else>
        <action name="If">
          <query target="default">
            <max_x>1</max_x>
            <min_y>40</min_y>
            <min_width>99</min_width>
          </query>
          <then>
            <action name="Iconify"/>
          </then>
          <else>
            <action name="If">
              <query target="default">
                <min_x>40</min_x>
                <max_y>1</max_y>
                <max_width>50</max_width>
              </query>
              <then>
                <action name="UnmaximizeFull"/>
                <action name="MoveResizeTo"><x>-0</x><y>-0</y><width>50%</width><height>50%</height></action>
              </then>
              <else>
                <action name="UnmaximizeFull"/>
                <action name="MoveResizeTo"><x>0</x><y>-0</y><width>100%</width><height>50%</height></action>
              </else>
            </action>
          </else>
        </action>
      </else>
    </action>
  </keybind>

  <!-- Run an application -->
  <keybind key="W-r">
    <action name="Execute">
      <command>rofi -show run</command>
    </action>
  </keybind>

  <!-- File manager (explorer) -->
  <keybind key="W-e">
    <action name="Execute">
      <startupnotify>
        <enabled>true</enabled>
        <name>Thunar</name>
      </startupnotify>
      <command>Thunar</command>
    </action>
  </keybind>

  <!-- Do a screenshot -->
  <keybind key="W-w">
    <action name="Execute">
      <startupnotify>
        <enabled>true</enabled>
        <name>spectacle</name>
      </startupnotify>
      <command>spectacle</command>
    </action>
  </keybind>

  <!-- Lock -->
  <keybind key="W-l">
    <action name="Execute">
      <startupnotify>
        <enabled>true</enabled>
        <name>Lock</name>
      </startupnotify>
      <command>i3lock</command>
    </action>
  </keybind>
</keyboard>
