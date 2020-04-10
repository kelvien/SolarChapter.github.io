✨☀️ Solar Chapter ☀️✨
===

## Technologies
Jekyll: Static site generator.

## Directories structure
All files are grouped by their function:
### Non-technical
1. [_teams](/_teams)

    Contains teams data. These variables are needed by a `team` to build the `teams` list and its own page:
    - `order`: Order of where it will show up in the `teams` page
    - `headerMenuName`: Name that will show up in the header menu
    - `locationImage`: Image that will be used to show in the `/teams` page
2. [_chapters](/_chapters)

    Contains chapters' projects data. These variables are needed by a `chapter` to build the `chapters` map and list and its own page:
    - `province`: Name of the province
    - `regency`: Name of the regency
    - `place`: Name of the place/village
    - `chapter`: Chapter number (Must be in number!)
    - `status`: Status of the project (Must be either "Completed" or "In Progress")
    - `chapterTitle`: Chapter's title used in the projects' list
3. [_data](/_data)

    Contains reusable data. i.e: Solar Chapter's projects' regencies coordinates
4. [content](/content)

    Contains all pages' content
All page content have a file extension, namely `.md` (Markdown). This type of file is used to format your text. See what formatting you can do to your text using this [cheatsheet](https://www.markdownguide.org/cheat-sheet/).
- File name normally follow the link's name. i.e: content of solarchapter.com/donate page should live under `content/donate.md`

### Technical
1. [assets](/assets)

    Contains assets data. i.e: logo, small images.
- All image resources for gallery/sizeable images use should be stored outside of this repository. See [Where to store image resources?](#where-to-store-image-resources) section
2. [_includes](/_includes)

    [Developer friendly] Contains repeatable component to be reused. i.e: header/footer
3. [_layouts](/_layouts)

    [Developer friendly] Contains layout files to be reused by your pages
4. [_sass](/_sass)

    [Developer friendly] Contains styling files for your pages

## Guide - How to?
### How to update a page's content?
1. Open [content](/content) and find the page's content you want to edit. File name should be similar or same with the page you want to edit.
2. You should see the following `key-value` pairs. The key names should be self-explanatory.
i.e:
```
title: "Chapter One: Water for Umutnana"
```
This means that this pair should correspond to the page's title. I would recommend to refer to the actual page's content and backtrack the content to the markdown file.
- Configuration are classified by two groups:
1. Page specific. Stored in the [content](/content) directory
    - `permalink`: Page's link URL. i.e: `/donate` will make the page be accessible through `solarchapter.com/donate`
    - `layout`: Page's layout
    - `title`: Page's title
    - `description`: Page's description. Used in page's metadata for SEO
    - `metadataImage`: Page's metadata image. Used in page's metadata for SEO
2. Layout specific. Stored in the [_layouts](/_layouts)
    - `menu-color`: Color of the menu. Either `dark` or `light`
    - `custom_css`: List of CSS files for the page
    - `custom_js`: List of JS files for the page
- Value can be in `html` format too for complex styling if needed.

### Adding a new project page?
Create a new `.md` file at [_chapters](/chapters) directory. Place the file based on the chapter number of the project.

Check the [first project page](/_chapters/one/water-for-umutnana.md) and use it as an example. Note that a project does not need a `permalink`. It's been configured at the [_config](/_config.yml) file.

### How to add a new pin in the chapters' map?
1. Add coordinates data into the [regencies coordinates](/_data/regencies_coordinates.yml) file. (Use Google Maps to find the regency's coordinates)
Note: The name of the regency **must be the same** as what is set in the chapter's `.md` file!
2. Done! Chapters' projects will appear in the map by the `regency` value defined in its file.

### How to add a new fundraising box in Donation page?
Fundraising box are generated by the `fundraisingLinks` variable set in the [chapter](_chapters) page.

### How to create a new landing page?
Follow [kain makna](/_chapters/three/kain-makna.md) page as an example
A landing layout will need these variables:
- `landingLogo`: Landing logo image URL
- `landingLogoTopLocation`: Landing logo location from the top in percentage
- `landingLogoLeftLocation`: Landing logo location from the left in percentage
- `landingLogoWidth`: Landing logo's width
- `landingLogoHeight`: Landing logo's height
- `landingLogoButton`: Landing logo's button right below the logo if needed
    - `title`: Button's text
    - `link`: Buttons' link URL
- `mainParagraph`: First paragraph in the landing page
- `sections`: List of sections in the landing page
    - `image`: Image to be displayed in the section
      `imagePosition`: Position of the image ("left"/"right")
      `content`: Content of the section

### <a id="where-to-store-image-resources"></a>Where to store image resources?
If possible, always serve files through Google Photos because repository is not designed to control revision of images. Other than that, storing images in the CDN will make them be highly available and accessed quicker.
1. Store images at Google Photos. Contact Solar Chapter for account access
- Upload media files (pictures/videos) at Solar Chapter's Google Photos account at the "SolarChapter.com Website" album. Contact Solar Chapter for account access.
- View the image and right-click the image and select "Copy image address". The image address should be hosted at `lh3.googleusercontent.com`. **Make sure that the image/album of the image is marked as share-able**
2. Store videos at Cloudinary. Contact Solar Chapter for account access 

## SEO
SEO is used for search engine and social media post's preview data. i.e: Google, Facebook/Twitter/Linkedin post preview
These variables are for SEO:
- `title`: Title of the page
- `description`: Description of the page
- `metadataImage`: Main image of the page. Normally shown in FB/Twitter/Linkedin's preview post

## Developer Notes
1. Don't forget to have `---` to start and end your `Markdown` files!
2. Read [Jekyll](https://jekyllrb.com/)
3. To set up local development environment:
```
jekyll serve --livereload
```
