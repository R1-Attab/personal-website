# Erwan ATTABA, personal website

A simple, fast personal website made of plain HTML, CSS and JavaScript.
There is nothing to install and no build step: the files in this folder *are* the website.

```
personal-website/
├── index.html      ← all the text of the site
├── styles.css      ← colors, fonts, layout
├── script.js       ← smooth scrolling, mobile menu, small animations
├── README.md       ← this guide
└── images/
    ├── profile-placeholder.svg   ← swap for your photo
    ├── project-placeholder.svg   ← swap for project photos
    ├── og-image.png              ← preview image for LinkedIn/WhatsApp shares
    └── favicon.svg               ← the little icon in the browser tab
```

---

## 1. Open the site on your computer

1. Open the `personal-website` folder in Finder (Mac) or File Explorer (Windows).
2. Double-click **`index.html`**.
3. It opens in your web browser. That's it, no internet connection needed.

After you edit a file, save it and press **Refresh** (⌘R on Mac, Ctrl+R on Windows) in the browser to see the change.

---

## 2. Put the project on GitHub

You only need to do this once. These steps use the GitHub website, so you don't need to use the command line.

1. Go to <https://github.com> and sign in.
2. Click the **+** in the top-right corner, then **New repository**.
3. Give it a name, for example `personal-website`. Leave it **Public** (or choose Private, Netlify works with both).
4. Do **not** tick "Add a README" (you already have one). Click **Create repository**.
5. On the next page, click the link **"uploading an existing file"**.
6. Open your `personal-website` folder, select **everything inside it** (`index.html`, `styles.css`, `script.js`, `README.md` and the `images` folder) and drag it into the browser window.
   Make sure you drag the *contents* of the folder, so that `index.html` sits at the top level of the repository and not inside another folder.
7. Scroll down, type a short message like "First version of my site", and click **Commit changes**.

**Later updates:** open the repository on GitHub, click **Add file → Upload files**, drag in the files you changed, and click **Commit changes**. The new files replace the old ones.

<details>
<summary>Prefer the command line? (optional)</summary>

From inside the `personal-website` folder:

```bash
git init
git add .
git commit -m "First version of my site"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/personal-website.git
git push -u origin main
```

For later updates: `git add .`, `git commit -m "Describe the change"`, `git push`.
</details>

---

## 3. Publish it on Netlify (free), with automatic updates

1. Go to <https://app.netlify.com> and sign up or log in. Choosing **Sign up with GitHub** is easiest.
2. On your dashboard, click **Add new project**, then **Import an existing project**.
3. Choose **GitHub** and allow Netlify to access your account if asked. You can limit access to just the `personal-website` repository.
4. Pick your `personal-website` repository from the list.
5. On the settings screen:
   - **Branch to deploy:** `main`
   - **Build command:** leave it **empty**
   - **Publish directory:** leave it **empty** (empty means the root of the repository, which is where `index.html` is)
6. Click **Deploy**. After about a minute you get an address like `https://something-random.netlify.app`.
7. Optional: under **Project configuration → Change project name** you can pick a nicer address, such as `erwan-attaba.netlify.app`. You can also connect your own domain under **Domain management**.

From now on, **every time you push or upload changes to GitHub, Netlify republishes the site automatically** within a minute or so.

**One last edit after your first deploy:** open `index.html`, find the lines near the top that contain `https://YOUR-SITE.netlify.app` (there are three), and replace that part with your real Netlify address. This makes the preview image appear when someone shares your link on LinkedIn or WhatsApp. Then upload `index.html` to GitHub again.

---

## 4. Change your text and images

Open the files in any text editor. **VS Code** (free, <https://code.visualstudio.com>) is a good choice, but Notepad or TextEdit work too. In TextEdit, choose **Format → Make Plain Text** first.

### Your text: `index.html`

Everything you read on the site is in `index.html`. Look for the comments marked **`EDIT ME`**:

| What | Where to look in `index.html` |
|---|---|
| Page title and Google/LinkedIn description | the `<title>` and `<meta ... description>` lines at the very top |
| Your one-line tagline | the `HERO` section, the line with `class="tagline"` |
| Longer bio | the `ABOUT` section, the `<p>` paragraphs |
| Skills list | the `ABOUT` section, each `<li>` under "What I do" |
| Projects | the `PROJECTS` section; each project is one `<article class="card">` block. Copy a whole block to add a project, delete one to remove it. Replace `href="#"` with a real link, or delete the "Read more" line. |
| Jobs | the `EXPERIENCE` section; each job is one `<li class="timeline-item">` block |
| Education | the list with `class="edu-list"` |
| Contact | the `CONTACT` section |

Only change the words **between** the tags, for example `<p>change this text</p>`. Leave the `<` `>` parts alone.

**Your phone number** is in the Contact section but hidden on purpose, because anyone on the internet can read this page. To show it, find the line with `tel:+33650059371` and remove the `<!--` at its start and the `-->` at its end.

### Your images: the `images` folder

Look for comments marked **`✏️ SWAP IMAGE`** in `index.html`.

- **Profile photo:** put a square photo (at least 600 × 600 pixels) in the `images` folder, for example `profile.jpg`. In `index.html`, change `src="images/profile-placeholder.svg"` to `src="images/profile.jpg"`.
- **Project images:** add landscape photos (16:9, for example 1280 × 720) such as `images/suriname.jpg`, then change each card's `src="images/project-placeholder.svg"` to point to your file. Also update the `alt="..."` text so it describes the photo, which helps screen-reader users and Google.
- **Share preview:** replace `images/og-image.png` with your own 1200 × 630 image, keeping the same file name.

Keep file names lowercase with no spaces (`my-photo.jpg`, not `My Photo.JPG`). Netlify treats `Photo.jpg` and `photo.jpg` as different files.

### Colors and fonts: `styles.css`

The colors are at the top of `styles.css`, under `:root` (light mode) and under `prefers-color-scheme: dark` (dark mode, used automatically when the visitor's computer is in dark mode). Change the color codes such as `#1a3fa8` (blue) and `#c8102e` (red).

The site uses each device's built-in system font (San Francisco on Apple, Segoe UI on Windows, Roboto on Android), so it loads instantly and works offline. If you want a specific font later, download its `.woff2` files into a `fonts` folder and ask me to wire it up.
