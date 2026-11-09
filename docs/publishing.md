# Publish the case study

The folder is intended to become an independent public repository named **saveor-case-study**. It is documentation-only: there is no build, package installation, application code, or standalone code demo.

## Media is integrated

The README includes three screenshots, a short GIF preview, and clickable posters for two recordings:

- `assets/demo/saveor-product-demo.mp4` — item creation, 49 seconds.
- `assets/demo/saveor-inventory-demo.mp4` — inventory search, sort, and filter, 25 seconds.

The MP4 files preserve the supplied recordings. HEIC screenshots have been converted to PNG. See the [demo manifest](../assets/demo/README.md) and [screenshot manifest](../assets/screenshots/README.md).

Poster links point to repository MP4 files, not embedded video players. If you prefer a hosted player, upload each recording to a public video host or repository release and replace the corresponding poster and text link targets in the README. Keep the GIF and posters in the repository. Test both links while signed out after publishing.

## Create your GitHub repository

Create an empty public repository named `saveor-case-study` under your account. From this folder, initialize Git and make the first commit:

```sh
git init -b main
git add README.md docs assets .gitignore
git diff --cached --stat
git diff --cached
git commit -m "Add SaveOr product and engineering case study"
```

Add the remote URL shown by GitHub with `git remote add origin YOUR_REPOSITORY_URL`, replacing the final argument, then run `git push -u origin main`. This guide does not create a repository or publish anything automatically.

Suggested repository description: **SaveOr CTO case study: inventory performance, payment reliability, and AI-assisted item creation.**

## Before sharing

Confirm the role and scale figures remain current. Include only public-facing product media and engineering explanations you can share. Keep the attribution intact. No open-source license is included because this repository does not grant rights to SaveOr’s private implementation or product assets.

Check README links, images, the architecture diagram, and the full recording in the published repository. Pin the repository on your profile when ready. The future standalone synthetic-data demonstration belongs in your separate repository and is intentionally absent here.
