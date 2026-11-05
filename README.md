# Jed Guzelkabaagac

Personal research website at https://jedml.com/, hosted on GitHub Pages from the master branch root. Keep CNAME set to jedml.com and retain .nojekyll. No dependencies or build step.

## Editing

- index.html: biography, affiliations, and publications.
- projects/index.html: research projects and code.
- blog/index.html: blog landing page; no posts published yet.
- assets/site.css: shared styling and responsive layouts.
- assets/portrait-sdr.jpg: 1200 × 1600 sRGB JPEG derived from the SDR base image of the original Display P3 MPO. It preserves the full frame, omits the HDR gain map and EXIF metadata, and uses an embedded sRGB profile. The original remains assets/portrait-oxford.jpeg.

Preview: python -m http.server 8765 --bind 127.0.0.1

## Adding a post or project page

Create blog/<slug>/index.html or projects/<slug>/index.html. Copy the head, navigation, skip link, and footer from its index; retain the active navigation item. Set a unique title, description, and canonical URL. Use one H1, a visible publication date in a time element, and a readable article width. Link the entry from its index. Interactive HTML/JS explanations and images can live beside the page. No backend or paid hosting is needed.

Affiliations use linked names rather than the protected Oxford logo. Project illustrations are schematic icons, not results. Earlier versions remain in Git history.
