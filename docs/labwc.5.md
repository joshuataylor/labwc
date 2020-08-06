% labwc(5)
% Johan Malm
% 24 July, 2020

# NAME

labwc - Configuration files

# CONFIGURATION

There are two configuration files which control the look and behaviour of
labwc, namely rc.xml and themerc. The configuration aims to be compatible with
Openbox, but there are some differences which are pointed out in this man page.

# RC.XML `<lab>`

Labwc specific settings which are not present in Openbox.

    <lab>
      <csd></csd>
      <keyboard>
        <layout></layout>
      </keyboard>
    </lab>

`csd` (__boolean__; default `no`)

:   Use client-side decorations for xdg-shell views.

`keyboard-layout` (__string__; not set by default)

:   Set `XKB_DEFAULT_LAYOUT`. See xkeyboard-config(7) for details.

# RC.XML `<theme>`

    <theme>
      <name></name>
    </theme>

`name` (__string__; default `Clearlooks`)

:   The name of the Openbox theme to use

# RC.XML `<keyboard>`

Describe key bindings.

    <keyboard>
      <keybind key="KEY-COMBINATION">
        ACTION
      </keybind>
    <keyboard>

`KEY-COMBINATION`

:   The key combination to bind to an **ACTION** in the format
    **modifier-key**, where supported **modifiers** include S (shift);
    C (control); A (alt); W (super). Unlike Openbox, multiple space-separated
    **KEY-COMBINATION** and key-chains are not supported.

Example:

    <keyboard>
      <keybind key="A-Escape">
        <action name="Exit"/>
      </keybind>
      <keybind key="A-Tab">
        <action name="NextWindow"/>
      </keybind>
      <keybind key="A-F3">
        <action name="Execute">
          <command>dmenu_run</command>
        </action>
      </keybind>
    <keyboard>

Default:

If no rc.xml file is found, the following default values will be used:

- Alt+Escape: Exit labwc  
- Alt+Tab: Cycle windows  
- Alt+F3: Launch dmenu  

# ACTIONS

Actions are used in key bindings.

Action syntax:

    <action name="NAME">
      OPTION
    </action>

where `NAME` is the name of the action as listed below, and `OPTION` is a set
of tags specific to each action as defined below.

`Execute`

:   Execute command specified by `<command>` option.

`Exit`

:   Exit labwc.

`NextWindow`

:   Cycle focus to next window.

# THEMERC

`window.active.title.bg.color`

:   Background for the focussed window's titlebar

`window.active.handle.bg.color`

:   Background for the focussed window's handle.

`window.inactive.title.bg.color`

:   Background for non-focussed windows' titlebars

# DEFINITIONS

The `handle` is the window decoration placed on the bottom of the window.

# EXAMPLES

## Example 1 - title bar configuration

    +-----------------------------------------+ ^
    |                                         | |
    |                                         | |
    |                                         | | h
    |                                         | |
    +-----------------------------------------+ v

    h = padding * 2 + font-vertical-extents


# SEE ALSO

labwc(1)