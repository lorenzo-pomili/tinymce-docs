---
layout: default
title: Creating custom Menu toolbar buttons
title_nav: Menu toolbar button
description: Creating custom Menu toolbar buttons for TinyMCE
keywords: toolbar toolbarbuttons buttons toolbarbuttonsapi
---

A toolbar menu button is a toolbar button that opens a menu when clicked. This menu can also contain submenus. This is useful for grouping together actions that would otherwise be several buttons on the toolbar. It can also be used to reduce visual clutter and save UI space, as menubar menu items and some toolbar buttons could be moved into a toolbar menu button. Potentially, all menubar menu items could be moved into toolbar menu buttons, allowing for the editor to be used without a menubar at all.

For example: The table plugin's `table` toolbar button opens a menu similar to the menubar Table menu.

## Config options

| Name | Value | Requirement | Description |
|------| ------| ------------| ----------- |
| fetch | (success: (menu) => void) => void  | required | Function that takes a callback which must be passed the list of options for the button's dropdown. |
| text | string | optional | Text to display if no icon is found. |
| icon | string | optional | {% include /misc/admon_predefined_icons_only.md %} |
| tooltip | string | optional | Text for button tooltip. |
| onSetup | (api) => (api) => void | optional | default: () => () => {} - Function that's invoked when the button is rendered. For details, see: [Using `onSetup`](#usingonsetup). |

## API

| Name | Value | Description |
|------| ------| ------------|
| isDisabled | ( ) => boolean | Checks if the button is disabled. |
| setDisabled | (state: boolean) => void | Sets the button's disabled state. |

## Menu button example and explanation

The following is a simple toolbar menu button example:

{% include live-demo.html id="custom-toolbar-menu-button" tab="js" %}

This example configures a toolbar menu button with the label `My Button` that opens the specified menu when clicked. The top-level menu contains two items. The first menu item inserts content when clicked and the second menu item opens a submenu containing two menu items which insert content when clicked.

The `fetch` function is called when the toolbar menu button's menu is opened. It is a function that takes a callback and passes it an array of menu items to be rendered in the drop-down menu. This allows for asynchronous fetching of the menu items.

{% include misc/onSetup.md %}