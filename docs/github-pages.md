Creating your own `github.io` website (known as **GitHub Pages**) is incredibly easy and entirely free. You can have a live website up and running in about 5 minutes.

Here is a step-by-step guide to building your first site.

---

## Step 1: Create a GitHub Account

If you don't have one already, head over to [GitHub](https://github.com) and sign up for a free account. Pick a username you like, as it will be part of your website's URL.

## Step 2: Create a New Repository

Think of a repository (or "repo") as a folder for your website's project files.

1. Log in to GitHub and click the **`+`** icon in the top-right corner, then select **New repository**.
2. **Repository name:** This is the most important step. You *must* name it exactly in this format:
`yourusername.github.io`
*(Replace `yourusername` with your actual GitHub username. For example, if your username is `octocat`, the repo name must be `octocat.github.io`).*
3. **Public/Private:** Select **Public**. (GitHub Pages is only free for public repositories).
4. **Initialize this repository with:** Check the box that says **Add a README file**.
5. Click **Create repository** at the bottom.

---

## Step 3: Create Your Homepage

Right now, your site just has a README file. Let's create the actual homepage.

1. Inside your new repository, click the **Add file** dropdown menu and select **Create new file**.
2. **Name your file:** Type `index.html`.
> *Note: It must be named exactly `index.html`. This tells the server that this file is the main entry point of your website.*


3. **Edit the file:** In the large text area below, paste some simple HTML code to start:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Awesome Website</title>
</head>
<body>
    <h1>Hello, World!</h1>
    <p>Welcome to my brand new GitHub Pages website.</p>
</body>
</html>

```

4. Scroll down to the bottom, add a commit message (like "Create index.html"), and click **Commit changes** (you might have to click it twice to confirm).

---

## Step 4: Turn on GitHub Pages (Usually Automatic)

Because you named your repository `yourusername.github.io`, GitHub usually activates the website automatically. However, it's always good to double-check:

1. Click on the **Settings** tab (the gear icon) at the top of your repository page.
2. In the left sidebar, scroll down to the "Code and automation" section and click on **Pages**.
3. Under **Build and deployment**, ensure the Source is set to **Deploy from a branch**, and the Branch is set to **main** (or `master`) and the folder is `/ (root)`.
4. Click **Save** if you had to change anything.

---

## Step 5: Visit Your Live Site!

At the top of that same **Pages** settings screen, you will see a box that says:
*"Your site is live at `https://yourusername.github.io/`"*.

Click that link, and you should see your "Hello, World!" page!

*(Note: It can sometimes take anywhere from 30 seconds to a couple of minutes for GitHub to build the site the very first time. If you get a 404 error, wait a minute and refresh).*

---

## Next Steps to Enhance Your Site

Once the basics are down, you can level up your site:

* **Add CSS and JS:** Create a `style.css` file for styling and a `script.js` file for interactivity, then link them inside your `index.html`.
* **Use a Template/Generator:** If you don't want to code from scratch, GitHub Pages natively supports **Jekyll**, a tool that turns Markdown files into blogs. Alternatively, you can build a site using React, Vue, or static site generators like Hugo, and deploy them to GitHub Pages.
* **Custom Domain:** You can buy a domain (like `myname.com`) and link it to your GitHub Pages site for free in the **Pages** settings menu.