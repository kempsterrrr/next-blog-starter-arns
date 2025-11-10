# Next.js Blog Starter - Deployed to Arweave with ArNS

A permanent, censorship-resistant blog deployed to Arweave's decentralized storage network and made accessible through ArNS (Arweave Name System).

This example demonstrates how to take Vercel's [Next.js blog-starter template](https://github.com/vercel/next.js/tree/canary/examples/blog-starter) and deploy it as an unstoppable application that will be accessible forever.

## What Makes This "Unstoppable"?

- **Permanent Storage** - Your blog is stored forever on Arweave for a one-time fee
- **Censorship-Resistant** - No single entity can remove or modify your content
- **Decentralized** - Accessible through AR.IO Network's 600+ independent gateways
- **Human-Readable URLs** - Access via ArNS domains like `myblog.arweave.net`

## Live Demo

View the deployed examples:

- [next-blog-starter-arns_kempsterrrr.ar.io](https://next-blog-starter-arns_kempsterrrr.ar.io)
- [next-blog-starter-arns_kempsterrrr.arweave.net](https://next-blog-starter-arns_kempsterrrr.arweave.net)

Same example, different gateway.


## Features

- **Next.js 15** with App Router and static export
- **TypeScript** for type safety
- **Tailwind CSS** with dark mode support
- **Markdown Blog Posts** using `remark` and `gray-matter`
- **Responsive Design** - Mobile-first approach
- **SEO Optimized** - Meta tags and OpenGraph support
- **Permanent Deployment** - One-command deployment to Arweave

## Quick Start

### Prerequisites

- Node.js 18 or higher
- An [Arweave wallet](https://www.wander.app/) with storage credits
- An [ArNS name](https://arns.app) (optional, for human-readable URLs)

### Installation

```bash
# Clone or create from template
npx create-next-app@latest my-blog --example blog-starter
cd my-blog

# Install permaweb-deploy
npm install --save-dev permaweb-deploy
```

### Local Development

```bash
# Start development server
npm run dev

# Build static site
npm run build

# Test static build locally
npx serve out
```

Visit [http://localhost:3000](http://localhost:3000) to see your blog.

## Deployment to Arweave

### Configure Static Export

The `next.config.js` is already configured for static export:

```javascript
module.exports = {
  output: 'export',
  images: { unoptimized: true },
  trailingSlash: true,
}
```

### Deploy

1. **Encode your wallet:**
   ```bash
   base64 -i wallet.json | pbcopy
   ```

2. **Deploy your blog:**
   ```bash
   DEPLOY_KEY=$(base64 -i wallet.json) npm run deploy
   ```

3. **Visit your ArNS URL** (e.g., `https://myblog.arweave.net`)

> **Note:** Update the `--arns-name` flag in `package.json` scripts to match your ArNS name.

## GitHub Actions (Recommended for Production)

For automated deployments on every push:

1. **Add GitHub Secret:**
   - Go to Settings → Secrets and variables → Actions
   - Create secret named `DEPLOY_KEY`
   - Paste your base64-encoded wallet

2. **Workflow is already configured** in `.github/workflows/deploy.yml`

3. **Push to main branch** to trigger deployment

## Project Structure

```
.
├── _posts/              # Markdown blog posts
├── public/              # Static assets (images, favicons)
├── src/
│   ├── app/             # Next.js App Router pages
│   ├── interfaces/      # TypeScript type definitions
│   └── lib/             # Utility functions
├── next.config.js       # Next.js configuration (static export)
└── package.json         # Dependencies and deploy scripts
```

## Adding New Blog Posts

Create a new `.md` file in `_posts/` with frontmatter:

```markdown
---
title: "My Permanent Blog Post"
excerpt: "This post will live forever on Arweave"
coverImage: "/assets/blog/my-image.jpg"
date: "2024-01-15T00:00:00.000Z"
author:
  name: "Your Name"
  picture: "/assets/blog/authors/avatar.jpg"
---

Your markdown content here...
```

The post will automatically appear on your blog after rebuilding.

## Learn More

- [Full Tutorial](https://docs.ar.io/guides/hosting-unstoppable-apps/hosting-a-blog) - Step-by-step guide
- [AR.IO Documentation](https://docs.ar.io) - Learn about the AR.IO Network
- [ArNS Documentation](https://docs.ar.io/arns) - Arweave Name System details
- [permaweb-deploy](https://github.com/permaweb/permaweb-deploy) - Deployment tool documentation

## Technologies Used

- [Next.js](https://nextjs.org/) - React framework
- [TypeScript](https://www.typescriptlang.org/) - Type safety
- [Tailwind CSS](https://tailwindcss.com) - Styling
- [remark](https://github.com/remarkjs/remark) - Markdown processing
- [gray-matter](https://github.com/jonschlinkert/gray-matter) - Frontmatter parsing
- [Arweave](https://arweave.org) - Permanent storage
- [AR.IO Network](https://ar.io) - Decentralized gateway network
- [permaweb-deploy](https://github.com/permaweb/permaweb-deploy) - Deployment tool

## Support

- [AR.IO Discord](https://discord.com/invite/HGG52EtTc2) - Community support
- [GitHub Issues](https://github.com/ar-io/docs/issues) - Report bugs or request features
