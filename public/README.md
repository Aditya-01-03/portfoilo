# Portfolio Static Site

## Deployment Instructions

### Deploying to GitHub Pages

1. **Push your code to GitHub**
   - Make sure your `portfoilo` folder is in your repository.
   - Commit and push all changes.

2. **Configure GitHub Pages**
   - Go to your repository on GitHub.
   - Click on **Settings** > **Pages**.
   - Under **Source**, select the branch (usually `main` or `master`) and set the folder to `/portfoilo`.
   - Save.

3. **Access your site**
   - After a few minutes, your site will be live at `https://<your-username>.github.io/<repo-name>/`.

### Notes
- The `.nojekyll` file ensures that GitHub Pages serves your site as plain static files.
- Make sure all your asset paths in HTML/CSS/JS are relative.

---

For other platforms (Netlify, Vercel, etc.), simply drag and drop the contents of the `portfoilo` folder into their deployment interface.