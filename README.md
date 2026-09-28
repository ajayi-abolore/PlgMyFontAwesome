# PlgMyFontAwesome

**PlgMyFontAwesome** is a LifeTechOCMS plugin that provides a local Font Awesome icon library for LifeTech themes, modules, plugins, and other interface components.

The plugin allows LifeTech applications to load Font Awesome from the local plugin installation instead of depending on an external CDN.

## Features

- Local Font Awesome CSS library.
- No external Font Awesome CDN dependency.
- Can be loaded from any LifeTech theme or interface.
- Uses the LifeTech plugin path helper.
- Suitable for themes, modules, plugins, admin interfaces, and frontend pages.
- Keeps icon assets within the LifeTech application.

## Installation

Install or copy the plugin into the LifeTech plugin directory:

```text
plugins/
└── PlgMyFontAwesome/
    └── Services/
        └── font-awesome.css
```

The exact plugin directory may vary depending on the LifeTech installation.

After installation, make sure the plugin is available through the LifeTech plugin path.

## Loading Font Awesome

Add the Font Awesome stylesheet to the `<head>` section of your theme, layout, module, or page:

```php
<link rel="stylesheet"
      href="<?= ltPluginPath() ?>/PlgMyFontAwesome/Services/font-awesome.css" />
```

### How it works

`ltPluginPath()` returns the base URL/path used to access installed LifeTech plugins.

The resulting path will point to:

```text
PlgMyFontAwesome/Services/font-awesome.css
```

This means the application does not need to hard-code the site's domain or installation path.

## Example

A typical LifeTech `<head>` section can include:

```php
<head>
    <meta charset="UTF-8">

    <meta name="viewport"
          content="width=device-width, initial-scale=1.0">

    <title>LifeTech</title>

    <link rel="icon"
          type="image/x-icon"
          href="<?= ltSiteHostAddress() ?>/storage/media/<?= ltSiteLogo() ?>">

    <link rel="stylesheet"
          href="<?= ltPluginPath() ?>/PlgMyFontAwesome/Services/font-awesome.css" />
</head>
```

## Using Icons

Once the stylesheet has been loaded, Font Awesome classes can be used in the page.

For example:

```html
<i class="fa-solid fa-house"></i>
```

Another example:

```html
<button type="button">
    <i class="fa-solid fa-user"></i>
    Profile
</button>
```

You can also use icons alongside LifeTech interface components:

```html
<a href="/admin">
    <i class="fa-solid fa-gauge"></i>
    Dashboard
</a>
```

The available icon classes depend on the Font Awesome version included in:

```text
Services/font-awesome.css
```

## Local Assets

The main stylesheet is:

```text
PlgMyFontAwesome/
└── Services/
    └── font-awesome.css
```

If the stylesheet references local Font Awesome font files, those files should remain in their expected relative locations inside the plugin.

For example:

```text
PlgMyFontAwesome/
└── Services/
    ├── font-awesome.css
    └── webfonts/
        ├── fa-solid-900.woff2
        └── ...
```

Do not move the referenced font files without updating the corresponding paths in `font-awesome.css`.

## Why Use the LifeTech Plugin?

Instead of loading Font Awesome directly from an external CDN:

```html
<link rel="stylesheet"
      href="https://cdnjs.cloudflare.com/.../all.min.css">
```

LifeTech can load the local plugin:

```php
<link rel="stylesheet"
      href="<?= ltPluginPath() ?>/PlgMyFontAwesome/Services/font-awesome.css" />
```

This provides a consistent asset location within the LifeTech installation and reduces dependence on an external CDN.

## CDN vs Local Plugin

### External CDN

```html
<link rel="stylesheet"
      href="https://cdnjs.cloudflare.com/.../all.min.css">
```

The browser must retrieve the stylesheet from an external service.

### LifeTech Plugin

```php
<link rel="stylesheet"
      href="<?= ltPluginPath() ?>/PlgMyFontAwesome/Services/font-awesome.css" />
```

The stylesheet is served through the LifeTech installation.

## Using With Other LifeTech Plugins

PlgMyFontAwesome can be used together with other LifeTech plugins.

For example, a page can load both Tailwind and Font Awesome:

```php
<script src="<?= ltPluginPath() ?>/PlgMyTailwind/Services/tailwind_4_cdn.js"></script>

<link rel="stylesheet"
      href="<?= ltPluginPath() ?>/PlgMyFontAwesome/Services/font-awesome.css" />
```

The two plugins provide different responsibilities:

```text
PlgMyTailwind
    └── Tailwind CSS

PlgMyFontAwesome
    └── Font Awesome icons
```

They can therefore be loaded independently or together.

## Example LifeTech Theme Head

```php
<head>
    <meta charset="UTF-8">

    <meta name="viewport"
          content="width=device-width, initial-scale=1.0">

    <title>LifeTech</title>

    <link rel="icon"
          type="image/x-icon"
          href="<?= ltSiteHostAddress() ?>/storage/media/<?= ltSiteLogo() ?>">

    <!-- LifeTech Tailwind plugin -->
    <script src="<?= ltPluginPath() ?>/PlgMyTailwind/Services/tailwind_4_cdn.js"></script>

    <!-- LifeTech Font Awesome plugin -->
    <link rel="stylesheet"
          href="<?= ltPluginPath() ?>/PlgMyFontAwesome/Services/font-awesome.css" />

    <style type="text/tailwindcss">
        @theme {
            --color-primary: #08cf72;
            --color-primary-dark: #06b85f;
            --color-primary-light: #0ee685;
        }
    </style>
</head>
```

## Requirements

- LifeTech OCMS
- PlgMyFontAwesome installed and accessible through the LifeTech plugin system.
- A browser with CSS and webfont support.

## Troubleshooting

### Icons are not displaying

First confirm that the stylesheet is being loaded:

```php
<link rel="stylesheet"
      href="<?= ltPluginPath() ?>/PlgMyFontAwesome/Services/font-awesome.css" />
```

Then check the browser's developer tools and verify that the CSS file returns successfully.

### CSS loads but icons do not appear

Check that the Font Awesome font files referenced by `font-awesome.css` are available.

For example:

```text
Services/
└── webfonts/
    └── fa-solid-900.woff2
```

Also check the browser Network tab for failed `.woff`, `.woff2`, or other font requests.

### `ltPluginPath()` does not produce the expected URL

Verify that the plugin is installed in the LifeTech plugin directory and that the LifeTech application is correctly configured.

You can temporarily inspect the generated path:

```php
<?= ltPluginPath() ?>
```

## License

Refer to the license and Font Awesome licensing terms applicable to the version distributed with this plugin.

## Author

**LifeTech OCMS**

Plugin:

```text
PlgMyFontAwesome
```
