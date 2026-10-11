# Java Quest

Learn Java with short lessons and a quiz game. Easy, Medium and Hard are multiple choice. Extreme makes you type the code yourself.

It is a plain web app: no build step, no server, no accounts. Your progress is saved on your device.

## What is in this folder

| File | What it does |
| --- | --- |
| `index.html` | The whole app: lessons, questions, game logic, styles |
| `manifest.webmanifest` | Lets phones install it like an app (name, colors, icons) |
| `sw.js` | Lets it work offline after the first visit |
| `icons/` | App icons |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are |
| `.github/workflows/build-apk.yml` | Builds an Android APK on GitHub and posts it as a download |

## 1. Put it on GitHub

No Git needed:

1. Sign in at github.com and tap **New repository**. Name it `java-quest`, keep it **Public**, and create it.
2. Tap **uploading an existing file** (or **Add file > Upload files**).
3. Unzip this folder first. Drag in everything, including the `icons` folder and the hidden `.nojekyll` file. If your file picker hides dotfiles, skip `.nojekyll`; the app still works.
4. Tap **Commit changes**.

With Git:

```bash
cd java-quest
git init
git add .
git commit -m "Java Quest"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/java-quest.git
git push -u origin main
```

## 2. Turn on GitHub Pages (gives you a real link)

1. In the repo, open **Settings > Pages**.
2. Under **Build and deployment**, set **Source** to **Deploy from a branch**.
3. Pick branch **main** and folder **/ (root)**, then **Save**.
4. Wait a minute. Your app is live at `https://YOUR-USERNAME.github.io/java-quest/`.

## 3. Install it on your phone

Open the link above on your phone, then:

- **iPhone (Safari):** Share button > **Add to Home Screen**.
- **Android (Chrome):** menu (three dots) > **Install app** or **Add to Home screen**.

It opens full screen with its own icon. After the first visit it also works without internet. The fonts download on first load; offline you will see a similar built-in font.

## 4. Get a real Android app (APK)

The file `.github/workflows/build-apk.yml` makes GitHub build an Android app for you, using [Capacitor](https://capacitorjs.com). It runs by itself every time you push to `main`.

If the `.github` folder did not upload (hidden folders often get skipped), add it by hand:

1. In your repo, tap **Add file > Create new file**.
2. In the name box, type `.github/workflows/build-apk.yml`. Typing the slashes creates the folders.
3. Paste in the contents of `build-apk.yml` from this zip and commit.

Then:

1. Open the **Actions** tab, pick **Build Java Quest APK**, and tap **Run workflow** (skip this if the push already started a run).
2. Wait about 5 to 10 minutes for the green check.
3. Open the repo home page and tap **Releases** in the right column (or the **Code** tab on mobile). Download `java-quest.apk` from the newest release.
4. Open the file on your Android phone and allow **install from unknown sources** when asked.

Good to know:

- **iPhone:** APK files only install on Android. On iPhone use the home-screen install in step 3. A real iOS app needs a Mac with Xcode and an Apple Developer account ($99 a year).
- **Play Store:** this builds a debug APK for installing on your own devices. Publishing to Google Play needs a signed release build and a one-time $25 developer fee.
- **If the release step fails with a permissions error:** open **Settings > Actions > General > Workflow permissions** and choose **Read and write permissions**.
- **If the build fails on the icon step:** that step is optional and will not stop the build. You will just get the default Android icon.
- **Updates:** each run publishes a new release with a higher number. Install the newest APK over the old one.

## Changing things

- **Add or edit questions and lessons:** open `index.html` and search for `/*DATA*/`. Everything between `/*DATA*/` and `/*END DATA*/` is the content. Multiple choice questions list the correct answer first; the app shuffles the choices.
- **Extreme challenges:** the `EXTREME` list in the same block. Each challenge has a prompt, optional starter code, an example solution and a list of patterns the typed code must match.
- **Colors:** the variables at the top of the `<style>` block.
- **After any change:** open `sw.js` and change `java-quest-v1` to `java-quest-v2` (then v3, and so on). That makes phones fetch the new version instead of the cached one.

To test on your computer, run `python3 -m http.server` in this folder and open `http://localhost:8000`.

## Reset progress

On the home screen, tap **Reset progress** at the bottom, then tap it again to confirm.
