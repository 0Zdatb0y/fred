# Fred the Fat Cat: website setup

This folder is a complete website: a memorial page for Fred (a.k.a. Fat Cat) where the family can upload photos and videos, write memories, view everything full size, and play a slideshow.

It uses two free services, and **both need an adult to create the accounts**:

- **Cloudinary** stores the photos and videos.
- **GitHub Pages** hosts the website itself.

Setup takes about 15 minutes. You only edit one file, `config.js`.

---

## Part 1: Cloudinary (photo and video storage)

1. Go to **cloudinary.com** and sign up for the free plan.
2. On the Cloudinary dashboard, find your **Cloud name** near the top and copy it.
3. Make an upload preset. This lets the website upload without a password.
   - Click the **gear icon (Settings)**, then **Upload**, then **Upload presets**, then **Add upload preset**.
   - Set **Signing mode** to **Unsigned**.
   - Give it a name, such as `fred_uploads`, and write it down.
   - Optional: set the **Folder** to `fred` so everything stays together.
   - Leave **Allowed formats** empty. The site also saves written memories as small text files, and a format list could block them.
   - Click **Save**.
4. Allow the website to list the photos.
   - Go to **Settings**, then **Security**.
   - Under **Restricted image types**, **untick "Resource list"**.
   - Click **Save**.

## Part 2: Put your Cloudinary details into the site

**Don't double-click `config.js`.** Windows will try to run it and show the error "'window' is undefined". Instead, **right-click it, choose Open with, then Notepad** (or **Choose another app**, then Notepad). Fill in the two values:

```js
window.FRED_CONFIG = {
  cloudName: "your-cloud-name",
  uploadPreset: "fred_uploads",
  tag: "fred"
};
```

Save the file.

## Part 3: GitHub Pages (the website)

1. Go to **github.com** and create an account. GitHub requires account holders to be 13 or older.
2. Click **+** at the top right, then **New repository**.
   - Name it `fred`, or whatever you like. That name becomes part of the web address.
   - Choose **Public**, because GitHub Pages is free for public repositories.
   - Click **Create repository**.
3. On the new repository page, click **uploading an existing file**. Drag in `index.html`, `config.js` and `README.md`, then click **Commit changes**.
4. Go to the repository's **Settings**, then **Pages**.
   - Under **Source**, choose **Deploy from a branch**.
   - Branch: **main**, folder: **/ (root)**. Click **Save**.
5. Wait one or two minutes. The site will be live at:
   **`https://<your-github-username>.github.io/fred/`**

Share that link with the family.

---

## Good to know

- **Anyone with the link can add photos and memories.** There's no login. That keeps it easy for family, but don't post the link publicly.
- **To remove something:** in Cloudinary, open **Media Library**, find the item and delete it. The site updates within about a minute.
- **New uploads can take up to a minute** to appear for other people. The person who uploaded sees theirs right away.
- **Size limits (Cloudinary free plan):**
  - Photos: any size works. The site shrinks them automatically to fit the 10 MB limit.
  - Videos: up to 100 MB upload directly. Bigger ones get compressed in the browser first. That takes about as long as the video plays and works best in Chrome or Edge. Videos over roughly 40 minutes won't fit.
- **Free plan storage** is roughly 25 GB in total, which holds a lot of cat photos.
- **Up to 1,000 photos and videos** (each counted separately) can be listed on the page.
- **Dates:** each photo shows when it was taken, using the camera data inside the file. If a file has no camera data, the page shows the file's own date instead.

## Files

| File | What it is |
|---|---|
| `index.html` | The whole website |
| `config.js` | Your Cloudinary details, the only file you edit |
| `README.md` | This guide |
