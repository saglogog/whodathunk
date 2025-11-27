+++
date = "2025-10-18T10:55:49+03:00"
draft = true
title = "Theming this website"
description = "Theming notes: CSS location, fonts, colors and sources/references/useful info."
summary = "Website's theming info."
slug = "theming-hugo"
tags = ['yorgos']
+++

- CSS location: In this case, I just added stuff in main.css in *themes\whodathunk-theme\assets\css\\**main.css***.

- Fonts: Used google's source sans 3 in the header (import in head and call it in css class like *font-family: 'Source Sans 3';*), Georgia in the body and Courier New in Hero and website intro. 

- Colors/Palette: Trying these out for a spin:
    - Idea 1: 
        - Accent0(?): #f1eeea
        - Links(?): #0F8B8D
        - Letters(?): #00151
        - Accent1(?): #F58A07 
        - Accent2(?): #006494
        - Accent3(?): #053225
        - Accent4(?): #5F758E
    - Idea 2:
        {{< figure
        src="palette-sample.png"
        alt="An idea for a palette"
        caption="An idea for a palette"
        width="500"
        class="ma0 w-75"
        >}}
        -- also use these (#f2f0e, #ebeadf) and alternate the use the red as bg with white letters
    - Idea 3 (**current**): mostly using 3 colors: 
      - #dc533d, 
      - #051627 and
      - #f1eeea.
      

{{< details summary="See what gemini says" >}}

Hugo offers a few primary locations for your **CSS** files, depending on whether you're working within a theme or adding custom styles to your site:

### Standard CSS Locations

1.  **`/assets` Directory (Recommended for new sites and themes):**

      * This is the modern location for CSS, Sass, JavaScript, and other resources that you want to process using Hugo's **Asset Pipelines** (Hugo Pipes).
      * The compiled or linked CSS often ends up in the `/public/resources` directory when the site is built.
      * For a new Hugo site, you'd typically place your main stylesheet in a path like `assets/css/style.css` (or `assets/sass/style.scss` if using Sass).
      * If you're creating or modifying a theme, the CSS would go in the theme's own `assets` directory: `themes/<YOUR_THEME_NAME>/assets/css/style.css`.

2. **`/static` Directory (For files to be copied directly):**

      * Any files in the root `/static` directory are copied directly to the root of the `/public` directory when the site is built, preserving the folder structure.
      * If you place CSS here, e.g., in `static/css/custom.css`, it will be available at `/css/custom.css` on your built site.
      * This location is often used for files that don't need processing, like `favicon.ico`, but it can still hold CSS, especially for older themes or simple projects.

### Referencing the CSS in Your Templates

Regardless of where you place the CSS, you must link it in your HTML templates, usually within the `<head>` tag of a file like `layouts/partials/head.html` or `layouts/_default/baseof.html`.


  * **For files in `/assets`:** You use Hugo's built-in functions to process and reference the asset. For a file like `assets/css/style.css`:

    ```html
    {{ $style := resources.Get "css/style.css" | resources.Minify | resources.Fingerprint }}
    <link rel="stylesheet" href="{{ $style.RelPermalink }}">
    ```

  * **For files in `/static`:** You use a standard HTML link tag with the path starting from the root:

    ```html
    <link rel="stylesheet" href="/css/custom.css">
    ```

    This example uses Hugo Pipes to retrieve, minify, and fingerprint the file for better performance and cache-busting.

For an introduction to setting up a custom theme with Hugo, you can watch this video: [Hugo Blog Tutorial: Setting up a custom theme](https://www.youtube.com/watch?v=w6_cQsTwd3Q).

{{< /details  >}}


[...]
