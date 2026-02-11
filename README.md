# Artist Portfolio Jekyll Site

A clean, elegant Jekyll site template for artists to showcase their work, CV, and creative practice.

## Features

- **Responsive Design**: Mobile-friendly layout with a focus on visual content
- **Rotating Gallery Component**: Click navigation through artwork with keyboard support (arrow keys)
- **Multiple Sections**: Landing page, About, CV, Galleries, and Blog
- **Gallery Lightbox**: Each gallery supports multiple images with titles and descriptions
- **Gallery Grid**: Browse all gallery collections on the galleries index page
- **Beautiful Typography**: Elegant serif fonts with refined spacing
- **Clean Aesthetics**: Minimalist design that emphasizes artwork

## Project Structure

```
jekyll-artist-site/
├── _config.yml              # Site configuration
├── _galleries/              # Gallery collection (rotating galleries)
│   └── series-one.md
├── _posts/                  # Blog posts
│   └── 2024-01-15-on-process-and-practice.md
├── _layouts/                # Page templates
│   ├── default.html
│   ├── page.html
│   ├── gallery.html
│   └── post.html
├── assets/
│   ├── css/
│   │   └── main.scss        # Main stylesheet with gallery styles
│   └── images/              # Add your artwork here
├── index.md                 # Landing page
├── about.md                 # About page
├── cv.md                    # CV/Resume page
├── galleries.md             # Galleries index
├── blog.md                  # Blog index
├── Gemfile                  # Ruby dependencies
└── .gitignore
```

## Setup Instructions

### Prerequisites

- Ruby 2.7 or higher
- Bundler

### Installation

1. Clone or download this template
2. Navigate to the project directory:
   ```bash
   cd jekyll-artist-site
   ```

3. Install dependencies:
   ```bash
   bundle install
   ```

4. Serve locally:
   ```bash
   bundle exec jekyll serve
   ```

5. Visit `http://localhost:4000` in your browser

## Adding Your Content

### Portfolio Images

1. Create folders under `assets/images/` for each gallery series:
   ```
   assets/images/
   ├── series-one/
   ├── series-two/
   └── ...
   ```

2. Add your images to these folders

3. Create corresponding gallery pages in `_galleries/` (see `series-one.md` for template)

### About Page

Edit `about.md` with your bio, background, and current work focus.

### CV

Edit `cv.md` with your education, exhibitions, awards, and experience. The template includes sections for:
- Education
- Solo Exhibitions
- Group Exhibitions
- Awards & Fellowships
- Teaching
- Publications & Press

### Blog Posts

Add new posts to the `_posts/` folder following the naming convention: `YYYY-MM-DD-post-title.md`

## Gallery Component Guide

The rotating gallery is the centerpiece for each gallery collection. Here's how it works:

### Featured Images

In `_galleries/your-gallery.md`, define your images:

```yaml
images:
  - url: /assets/images/series-one/image-1.jpg
    caption: "Artwork Title"
    description: "Medium and year"
  - url: /assets/images/series-one/image-2.jpg
    caption: "Another Work"
    description: "Additional details"
```

### Navigation

- **Click Buttons**: Use Previous/Next buttons to navigate
- **Keyboard**: Use arrow keys (← and →) for navigation
- **Counter**: Shows current image position (e.g., "1 / 5")
- **Captions**: Each image can have a title and description

## Styling

The site uses CSS custom properties (variables) for easy theming. Edit these in `assets/css/main.scss`:

```scss
:root {
  --primary: #1a1a1a;      /* Text and primary color */
  --accent: #d4af37;       /* Gold accent for hover states */
  --light-bg: #fafaf8;     /* Light background */
  --border: #e0e0e0;       /* Border color */
  --text: #2c2c2c;         /* Main text */
  --text-light: #666;      /* Secondary text */
}
```

Customize these colors to match your brand or aesthetic.

## Deployment

### GitHub Pages

1. Push your repository to GitHub
2. In repository settings, enable GitHub Pages
3. Select the `main` branch as your source
4. Your site will be available at `username.github.io/repo-name`

### Other Hosting

- Netlify: Connect your GitHub repo, no additional configuration needed
- Vercel: Similar setup to Netlify
- Traditional hosting: Build locally with `jekyll build` and upload the `_site/` folder

## Tips for Artists

- **Image Optimization**: Compress images before uploading for faster load times. Tools like ImageOptim or TinyPNG work well.
- **Descriptive Alt Text**: Always add captions and descriptions to your gallery images for accessibility
- **Mobile Testing**: Check your site on mobile devices to ensure images display well
- **SEO**: The site includes Jekyll SEO Tag plugin. Add descriptions to your galleries and posts for better search visibility
- **Print CV**: Your CV page can be printed to PDF directly from the browser (Cmd+P / Ctrl+P)

## Customization Ideas

- Add a contact form
- Include video in galleries
- Create a testimonials/press section
- Add social media links
- Create an archive page for past shows
- Add tags/filtering to galleries
- Include exhibition images with artwork details

## Troubleshooting

**Gallery images not showing?**
- Check that image paths are correct and relative to the site root
- Ensure images are in the `assets/images/` folder
- Verify the image URL in your gallery front matter

**Styles not applying?**
- SCSS files need to be processed by Jekyll
- Make sure CSS file starts with `---` (empty front matter)
- Clear Jekyll cache: `rm -rf .jekyll-cache`

**Keyboard navigation not working?**
- Check browser console for JavaScript errors
- Ensure you're focused on the page (not a form input)

## Support & Resources

- [Jekyll Documentation](https://jekyllrb.com/docs/)
- [Liquid Template Language](https://shopify.github.io/liquid/)
- [GitHub Pages with Jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll)

---

Happy creating! If you have questions about modifying this template or want to add new features, the Jekyll documentation and community are great resources.
