# hellodrinkbot.com

The source for [hellodrinkbot.com](https://hellodrinkbot.com) — The Hello World of Cocktail Robotics Culture.

Built with [Hugo](https://gohugo.io) and deployed to [Cloudflare Pages](https://pages.cloudflare.com).

## Local Development

1. Install Hugo: `brew install hugo`
2. Clone this repo
3. Run the dev server: `hugo serve`
4. Open `http://localhost:1313`

## Deploying

Push to the `main` branch. Cloudflare Pages builds and deploys automatically.

git add . && git commit -m "your message" && git push

## Adding a Post

```bash
# Create a new post
hugo new content posts/my-post-title.md
vim content/posts/my-post-title.md
git add . && git commit -m "new post: my post title" && git push
```

Posts live in `content/posts/`. Pages (like About, Links) live in `content/pages/`.

## Project Links

- Main GitHub repo (hardware + software): https://github.com/RichGibson/hellodrinkbot
- Discord: https://discord.gg/HhaduD6ag4
- Facebook group: https://www.facebook.com/groups/602734573508700/
