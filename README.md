# Portfolio site

Static site. No build step. Files:

```
index.html                  home page
style.css                   all styling
projects/*.html             one page per project
assets/<project>/           images and videos (create as needed)
Prithvi_Vashisht_Resume.pdf resume linked from the home page (add this file)
```

## Preview locally

```
cd portfolio
python3 -m http.server 8000
```

Open http://localhost:8000.

## Deploy to GitHub Pages

1. Create a GitHub repository. For a URL of `https://<username>.github.io`, name it exactly `<username>.github.io`. Any other name gives `https://<username>.github.io/<repo-name>/`.
2. Upload the contents of this folder so `index.html` sits at the repository root.
   - Web: repository page, Add file, Upload files, drag everything in, Commit.
   - Git:
     ```
     cd portfolio
     git init
     git add .
     git commit -m "Initial site"
     git branch -M main
     git remote add origin https://github.com/<username>/<repo>.git
     git push -u origin main
     ```
3. Repository Settings, Pages. Source: Deploy from a branch. Branch: `main`, folder `/ (root)`. Save.
4. Wait 1 to 2 minutes. The URL appears at the top of the Pages settings.

Updates: commit and push changed files. The site redeploys automatically.

## Adding media

Video:

```html
<figure class="media">
  <video controls preload="metadata" poster="../assets/ball-tracking/poster.jpg">
    <source src="../assets/ball-tracking/demo.mp4" type="video/mp4">
  </video>
  <figcaption>Caption.</figcaption>
</figure>
```

Image:

```html
<figure class="media">
  <img src="../assets/autoslug-hand/render.jpg" alt="Description">
  <figcaption>Caption.</figcaption>
</figure>
```

Replace the `<div class="slot">` block in the matching project page. Paths from `projects/` pages start with `../`.

Limits: GitHub rejects single files over 100 MB and recommends repositories under 1 GB. Compress videos to H.264 MP4, or embed a YouTube link with an `<iframe>`.

## Adding a project

1. Copy `projects/slugbotics-arm.html` to `projects/<new-name>.html`.
2. Edit title, facts, and sections.
3. Copy a `<a class="card">` block in `index.html` and point `href` to the new page.
