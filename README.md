# Storyblok Field-Type Heroicons

This field-type allows users to choose icons with each of the available icon styles from [Iconify](https://iconify.design/).

Name | Description                                  | Author
------------ |----------------------------------------------| -------------
Iconify | Allows users to select any icon from Iconify | [Jean-Philippe Kha](https://github.com/jpkha)

![plugin-iconify](plugin-iconify.gif)

## Usage

Search and select your desired icon.

Returns an object with the icon name:

```
{
  "plugin": "iconify",
  "icon": "<icon name>",
  ...
}
```


## How to use ?
You can check [https://github.com/iconify/iconify](https://github.com/iconify/iconify) on how to use Iconify inside your project.

From the plugin, you got a value, for example, `logos:storyblok` then you can use it dynamically by using the Iconify component from your favorite framework.