# Rotating Gallery Implementation Guide

## How the Gallery Works

The rotating gallery component displays images one at a time with navigation controls. Users can browse through artwork using buttons or keyboard arrows.

## Gallery Structure

Each gallery is a separate collection item in `_galleries/your-name.md`:

```yaml
---
layout: gallery
title: Series Name
permalink: /gallery/series-name/
thumbnail: /assets/images/series-name/thumb.jpg
images:
  - url: /assets/images/series-name/image-1.jpg
    caption: "Artwork 1"
    description: "Medium, Year"
  - url: /assets/images/series-name/image-2.jpg
    caption: "Artwork 2"
    description: "Medium, Year"
---

## About This Series

[Write about your work here...]
```

## Creating a New Gallery

1. **Create the folder** for your images:
   ```
   assets/images/your-gallery-name/
   ```

2. **Add your images** to this folder

3. **Create the gallery file** in `_galleries/`:
   - Copy `_galleries/series-one.md`
   - Rename to `_galleries/your-gallery-name.md`
   - Update the YAML front matter with your images and metadata

4. **Test locally**:
   ```bash
   bundle exec jekyll serve
   ```
   Visit `http://localhost:4000/gallery/your-gallery-name/`

## Image Front Matter Details

### Required Fields

- **url**: Path to the image relative to site root
  - Example: `/assets/images/series-name/image-1.jpg`

### Optional Fields

- **caption**: Title or name of the artwork
- **description**: Medium, year, dimensions, or other details

Example:
```yaml
images:
  - url: /assets/images/paintings/piece-1.jpg
    caption: "Untitled (2024)"
    description: "Oil on canvas, 48 × 36 inches"
  - url: /assets/images/paintings/piece-2.jpg
    caption: "Study in Blue"
    description: "Acrylic on paper, 2024"
```

## JavaScript Navigation

The gallery includes automatic navigation handling:

### Features

- **Previous Button**: Go to previous image
- **Next Button**: Go to next image
- **Keyboard Support**: Use arrow keys (← →) to navigate
- **Wrap Around**: Gallery loops (last image → first image and vice versa)
- **Counter**: Shows position (e.g., "2 / 5")
- **Dynamic Captions**: Caption and description update with each image

### How It Works

The gallery JavaScript (in `gallery.html` layout):
1. Gets all gallery items
2. Tracks current index
3. Hides non-active items (opacity: 0)
4. Shows active item (opacity: 1)
5. Updates counter display
6. Updates caption if available

## Gallery Grid Page

The `/galleries` page displays all your gallery series:

```
[Gallery 1]  [Gallery 2]  [Gallery 3]
[Gallery 4]  [Gallery 5]  [Gallery 6]
```

Each gallery card:
- Shows the first image or thumbnail
- Links to the full rotating gallery
- Responsive grid that adapts to screen size

## Image Optimization Tips

For best performance:

1. **Resize large images**: 
   - Keep web images to 1200-1500px max width
   - Maintain aspect ratio

2. **Compress without losing quality**:
   - Use TinyPNG, ImageOptim, or similar tools
   - Aim for 50-200KB per image

3. **Use appropriate formats**:
   - JPG for photographs
   - PNG for graphics with transparency
   - WebP for modern browsers (optional)

4. **Consistent dimensions**:
   - Keep images in same aspect ratio for better gallery appearance
   - Different ratios work but may look irregular

## Styling the Gallery

The gallery styles are in `assets/css/main.scss`. Key classes:

```scss
.rotating-gallery {
  /* Container for the entire gallery */
}

.gallery-container {
  /* Image display area */
  aspect-ratio: 4 / 3;  /* Change this ratio to match your images */
  max-width: 700px;
}

.gallery-item {
  /* Individual image */
  opacity: 0;  /* Hidden by default */
}

.gallery-item.active {
  opacity: 1;  /* Visible when active */
}

.gallery-nav-btn {
  /* Previous/Next buttons */
}
```

### Customizing Gallery Dimensions

Change the gallery container aspect ratio in `main.scss`:

```scss
.gallery-container {
  aspect-ratio: 16 / 9;  /* For widescreen images */
  /* or */
  aspect-ratio: 1 / 1;   /* For square images */
  /* or */
  aspect-ratio: 3 / 4;   /* For portrait images */
}
```

## Multiple Galleries

Create as many galleries as you want:

- Create new folder: `assets/images/series-two/`
- Add images to folder
- Create file: `_galleries/series-two.md`
- Update front matter with your images
- Gallery automatically appears in `/galleries` grid

Example structure:
```
_galleries/
├── series-one.md
├── series-two.md
├── series-three.md
└── recent-work.md

assets/images/
├── series-one/
├── series-two/
├── series-three/
└── recent-work/
```

## Troubleshooting

### Images don't appear

1. Check image paths in YAML:
   - Should start with `/`
   - Should include full path: `/assets/images/folder/image.jpg`

2. Check file exists:
   - Navigate to `http://localhost:4000/assets/images/folder/image.jpg`
   - Should display the image directly

3. Check Jekyll cache:
   ```bash
   rm -rf .jekyll-cache _site
   bundle exec jekyll serve
   ```

### Navigation buttons don't work

1. Check browser console for errors (F12 or Cmd+Option+I)
2. Verify JavaScript section in `_layouts/gallery.html` is intact
3. Make sure you're using the `gallery` layout

### Captions don't update

1. Check image front matter has `caption` field
2. Verify syntax: `caption: "Your caption"` (with quotes)
3. Check browser console for JavaScript errors

## Advanced Customization

### Adding Image Metadata

Store additional data in YAML:

```yaml
images:
  - url: /assets/images/paintings/work-1.jpg
    caption: "Study One"
    description: "Oil on canvas"
    price: "$1,500"
    sold: false
    year: 2024
```

Then reference in layout:
```liquid
<p>Price: {{ image.price }}</p>
```

### Custom Styling per Gallery

Add CSS classes in front matter:
```yaml
gallery_class: "landscape"
```

Then style:
```scss
.rotating-gallery.landscape .gallery-container {
  aspect-ratio: 16 / 9;
}
```

### Adding Search/Filter

Could be extended to filter galleries by:
- Year
- Medium (painting, sculpture, etc.)
- Title
- Status (sold, available, etc.)

This would require additional JavaScript but uses the same image structure.

---

The gallery component is intentionally kept simple and accessible. It works with keyboard navigation, responsive on mobile, and doesn't require external libraries. Feel free to extend it to fit your needs!
