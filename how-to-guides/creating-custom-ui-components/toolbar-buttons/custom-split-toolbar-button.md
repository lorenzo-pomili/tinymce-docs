---
layout: default
title: Creating custom Split toolbar buttons
title_nav: Split toolbar button
description: Creating custom Split toolbar buttons for TinyMCE
keywords: toolbar toolbarbuttons buttons toolbarbuttonsapi
---

A split button contains a basic button and a menu button, wrapped up into one toolbar item. Clicking the menu button section opens a dropdown list. The basic button section and the menu items can be configured to trigger different actions when clicked.

## Config options

| Name         | Value                             | Target component  | Requirement | Description                                                                                                                        |
|--------------|-----------------------------------|-------------------|-------------|------------------------------------------------------------------------------------------------------------------------------------|
| text         | string                            | Primary button    | optional    | Text displayed if no icon is found.                                                                                                |
| icon         | string                            | Primary button    | optional    | {% include /misc/admon_predefined_icons_only.md %}                                                                                                       |
| onAction     | (api) => void                     | Primary button    | required    | Function invoked when the basic button section is clicked.                                                                         |
| select       | (value: string) => boolean        | Choice menu items | optional    | default: false - Function run on each option when the menu is opened to determine if it should be highlighted as active.           |
| columns      | number or `'auto'`                            | Drop-down menu    | optional    | default: 1 - Number of columns for the list of options. When set to more than 1 column, only the icon for each item will be shown. |
| fetch        | (success: (menu) => void) => void | Drop-down menu    | required    | A callback function that should be passed a list of [choice menu items](#choicemenuitems) for the dropdown menu.                                              |
| onItemAction | (api, value) => void              | Choice menu items | required    | Function invoked when a dropdown list option is clicked. The `value` is passed from the selected choice menu item.                    |
| onSetup      | (api) => (api) => void            | All               | optional    | default: () => () => {} - Function invoked when the button is rendered. For details, see: [Using `onSetup`](#usingonsetup).                                                           |

## API

| Name | Value | Description |
|------| ------| ------------|
| isDisabled | ( ) => boolean | Checks if button is disabled. |
| setDisabled | (state: boolean) => void | Sets the button's disabled state. |
| isActive| ( ) => boolean | Checks the button's toggle state. |
| setActive | (state: boolean) => void | Sets the button's toggle state. |

## Split button example and explanation

The following example sets up a split button with a text label and a static dropdown menu.

{% include live-demo.html id="custom-toolbar-split-button" tab="js" %}

A split button is similar to a basic button in that they both require an `onAction` callback. The `onAction` callback function should take the button's API and return nothing. It is called when the basic button section is clicked. In this example, `onAction` calls `editor.insertContent(value)` which inserts the given content into the editor.

`onItemAction` is called when a menu item is clicked. The callback function is passed the split button's API and the *value* of the selected menu item. Nothing should be returned. The example calls `editor.insertContent(value)` to insert the *value* into the editor's content.

The `fetch` function is called whenever the split button's drop-down menu is opened. It is a function that takes a callback and passes it an array of menu items to be rendered in the button's drop-down menu. This allows for asynchronous fetching of the menu items.

{% include components/choice-menu-items.md %}

{% include misc/onSetup.md %}