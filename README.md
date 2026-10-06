# Noey website

The public waitlist page for Noey: one static file (`index.html`) with no build step, hosted for free on GitHub Pages. It is kept separate from the app repo, so the two can't break each other.

## Publish it on GitHub Pages (free)

1. **Create a free GitHub organisation** named `getnoey` (github.com → your avatar → Your organizations → New organization → Free plan). The site will live at `https://getnoey.github.io`.
2. **Create a public repo** in that organisation named exactly `getnoey.github.io`. Pages on a free plan needs a public repo, which is fine here because the page holds nothing secret.
3. **Push this folder** from `C:\Magic\noey-site`:

   ```bash
   git init -b main
   git add .
   git commit -m "Waitlist page"
   git remote add origin https://github.com/getnoey/getnoey.github.io.git
   git push -u origin main
   ```

4. In the repo, open **Settings → Pages** and check that the source is *Deploy from a branch*, `main`, `/ (root)`. The site goes live within a minute or two.

`.nojekyll` tells GitHub to serve the files as they are, without running Jekyll over them.

## Connect the waitlist form (free)

GitHub Pages can't receive form posts, so submissions go to [Formspree](https://formspree.io). Its free plan takes 50 submissions a month, which is plenty for now.

1. Sign up at formspree.io and create a form. It gives you an endpoint like `https://formspree.io/f/abcdwxyz`.
2. In `index.html`, near the bottom, set `CONFIG.formEndpoint` to that URL and `CONFIG.contactEmail` to the address you want people to write to.
3. Push again. Submissions show up in the Formspree dashboard and in your inbox, and you can export them as CSV.

Until `formEndpoint` is set, the form tells visitors it isn't connected yet and sends nothing.

## Before you share the link

- [ ] Confirm the sentence under **"Your data stays where it is"** (marked `CONFIRM` in the HTML) matches exactly what the desktop app does with query results.
- [ ] Set `formEndpoint` and `contactEmail`, then send yourself a test submission.
- [ ] Open the live page on your phone.

## Adding a domain later

When you buy `getnoey.com` (about $10 a year), add it under **Settings → Pages → Custom domain**, then follow GitHub's DNS instructions. The `getnoey.github.io` address keeps working and redirects to the domain.
