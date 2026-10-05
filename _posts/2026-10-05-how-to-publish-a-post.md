---
title: How to publish a post on this site
description: One Markdown file, one pull request. The steps, and the four mistakes that stop a post from showing up.
date: 2026-10-05 20:00:00 +0400
categories: [Club, Guides]
tags: [writing, github]
pin: true
---

Every post on this site is one Markdown file in our GitHub repo. When a file lands on the `main` branch, GitHub Actions builds the site and publishes it. That takes about a minute. You don't need to install anything to write a post.

## 1. Make the file

In the repo, open the `_posts` folder and add a file named like this:

```text
2026-10-12-picoctf-web-writeup.md
```

The date comes first, then a short name with dashes. The short name becomes the link, so this one ends up at `/posts/picoctf-web-writeup/`.

## 2. Put this at the top of the file

```yaml
---
title: picoCTF web challenges write-up
date: 2026-10-12 19:00:00 +0400
categories: [Write-ups, CTF]
tags: [web, picoctf]
---
```

Then write the post under it in normal Markdown. Use `##` for section headings, because the page title is already the big heading.

For code and commands, put the language after the three backticks so it gets colours:

````markdown
```python
print("hello")
```
````

## 3. Add images (if you have them)

Put them in a folder named after your post, for example `assets/img/posts/picoctf-web-writeup/`. Then link them with the full path:

```markdown
![Burp Suite showing the login request](/assets/img/posts/picoctf-web-writeup/burp.png)
```

Write what the image shows inside the square brackets. Screen readers read it out, and it shows up if the image fails to load.

## 4. Send it

The easy way, all on the GitHub website:

1. Open the `_posts` folder in the repo.
2. Click **Add file**, then **Create new file**.
3. Type the file name, paste your post, and click **Commit changes**. GitHub offers to open a pull request for you.
4. When the pull request is merged, the **Build and Deploy** action runs and your post goes live.

To fix a typo later, open the post on the site and click **Edit this post** at the bottom.

## Why a post doesn't show up

Open the **Actions** tab in the repo. A red run means the build failed, and the log says why. These four cause most of it:

- **The date is in the future.** Jekyll skips future posts without any error. Use UAE time with `+0400` and a time that has already passed.
- **A link uses `http://`.** The build checks every link and fails on plain `http://`. Use `https://`.
- **An image path is wrong.** The build fails on any image or internal link that points to a file that doesn't exist. Paths are case-sensitive, so `Burp.png` and `burp.png` are different files.
- **The front matter is broken.** The `---` lines must be the very first and last lines of that block, and `categories` and `tags` need the square brackets.

## Preview it on your laptop (optional)

If you have Ruby installed:

```bash
git clone https://github.com/ADU-Cybersecurity-Club/adu-cybersecurity-club.github.io
cd adu-cybersecurity-club.github.io
bundle install
bundle exec jekyll serve
```

Then open `http://127.0.0.1:4000` in your browser. The page reloads when you save the file.
