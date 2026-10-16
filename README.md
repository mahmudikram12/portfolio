# Website upload package

This package contains the updated static website and the files needed to publish it from a GitHub repository using GitHub Pages.

## Files

- `index.html` — the website, with browser-side editor storage changed to use IndexedDB to reduce localStorage quota errors. Existing page content and embedded images have been retained.
- `.nojekyll` — tells GitHub Pages not to run Jekyll processing on the site.

## Publish using GitHub Pages

1. Download and extract this ZIP file on your computer.
2. Open the GitHub repository that hosts your website.
3. Back up the current website file by downloading the existing `index.html` before replacing it.
4. Upload the new `index.html` and `.nojekyll` to the **repository root** (the top-level folder, not a subfolder). Replace the existing `index.html` when GitHub asks.
5. Commit the changes to the branch used for GitHub Pages (commonly `main`).
6. In the repository, open **Settings → Pages**. Under **Build and deployment**, choose **Deploy from a branch**, select the correct branch (commonly `main`) and folder (`/(root)`), then save. If Pages is already configured this way, you do not need to change it.
7. Wait for the Pages deployment to finish under the repository's **Actions** tab, then reload the published site. If an old version remains, hard-refresh the page or test in a private/incognito window.

## Important note about Admin edits

This fix moves the large saved editor state to IndexedDB in the current browser, which helps avoid the browser's localStorage size limit. It does **not** automatically publish Admin edits to every visitor or synchronize edits across devices. For shared online updates, the site needs a properly configured cloud/database service or an admin workflow that commits changes to the GitHub repository. Do not put a private GitHub access token in client-side website code.
