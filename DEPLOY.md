# Deploying PromptFill to Vercel

This guide provides step-by-step instructions for deploying the PromptFill application to Vercel.

## Prerequisites

Before deploying, ensure you have:
- A [Vercel account](https://vercel.com/signup) (free tier is sufficient)
- Your PromptFill repository on GitHub
- Node.js installed locally (for CLI deployment)

## Deployment Notes

**Important deployment characteristics:**
- ✅ This app deploys at the **root domain** (no subdirectory needed)
- ✅ **No Vite base setting** is required (already configured with `base: './'`)
- ✅ **No SPA rewrite rules** needed (app does not use React Router)
- ✅ Simple static site deployment - works out of the box

## Method 1: Deploy via Vercel Dashboard (Recommended for First-Time Users)

### Step 1: Connect Your Repository

1. Go to [Vercel Dashboard](https://vercel.com/dashboard)
2. Click **"Add New"** → **"Project"**
3. Click **"Import Git Repository"**
4. Authorize Vercel to access your GitHub account if not already done
5. Select the **PromptFill** repository from the list

### Step 2: Configure Project Settings

Vercel will auto-detect the project configuration from `vercel.json`. You can verify:

- **Framework Preset**: Vite
- **Build Command**: `npm run build` (from vercel.json)
- **Output Directory**: `dist` (from vercel.json)
- **Install Command**: `npm install` (auto-detected)

No additional configuration is needed. The `vercel.json` file handles all settings.

### Step 3: Deploy

1. Click **"Deploy"**
2. Wait for the build process to complete (typically 1-2 minutes)
3. Once deployed, you'll receive:
   - A production URL (e.g., `promptfill.vercel.app`)
   - Automatic HTTPS certificate
   - Preview URLs for all branches

### Step 4: Verify Deployment

1. Click on the deployment URL to open your app
2. Test the application functionality:
   - Template creation and editing
   - Word bank management
   - Image uploads and previews
   - Export functionality

## Method 2: Deploy via Vercel CLI

### Step 1: Install Vercel CLI

```bash
npm install -g vercel
```

### Step 2: Login to Vercel

```bash
vercel login
```

Follow the prompts to authenticate via email or GitHub.

### Step 3: Navigate to Project Directory

```bash
cd /path/to/PromptFill
```

### Step 4: Deploy to Preview (Optional)

For a preview deployment:

```bash
vercel
```

This creates a unique preview URL without affecting production.

### Step 5: Deploy to Production

For production deployment:

```bash
vercel --prod
```

The CLI will:
1. Detect the project configuration from `vercel.json`
2. Upload your code
3. Build the project using `npm run build`
4. Deploy the `dist` directory
5. Provide you with the deployment URL

### CLI Deployment Output Example

```
Vercel CLI 28.0.0
🔍  Inspect: https://vercel.com/your-team/promptfill/xxx
✅  Production: https://promptfill.vercel.app [copied to clipboard]
```

## Automatic Deployments

Once connected, Vercel automatically:
- Deploys every push to the `main` branch → **Production**
- Deploys every push to other branches → **Preview**
- Deploys every pull request → **Preview** (with unique URL)

## Custom Domain (Optional)

To use a custom domain:

1. Go to your project in Vercel Dashboard
2. Navigate to **Settings** → **Domains**
3. Add your domain (e.g., `promptfill.com`)
4. Follow DNS configuration instructions
5. Vercel handles SSL certificates automatically

## Environment Variables

This application runs entirely in the browser using localStorage. No environment variables are required for deployment.

If you need to add environment variables in the future:

**Via Dashboard:**
1. Go to **Settings** → **Environment Variables**
2. Add variables with appropriate scope (Production, Preview, Development)

**Via CLI:**
```bash
vercel env add VARIABLE_NAME
```

## Troubleshooting

### Build Fails

If the build fails:
1. Check the build logs in Vercel Dashboard
2. Ensure `package.json` dependencies are correct
3. Test build locally: `npm run build`
4. Check Node.js version compatibility (requires Node.js 18+)

### App Shows Blank Page

If deployed app shows a blank page:
1. Check browser console for errors
2. Verify `dist` directory contains `index.html` and assets
3. Ensure `base: './'` is set in `vite.config.js` (already configured)

### 404 Errors

This app doesn't require SPA rewrites since it doesn't use React Router. If you see 404s:
1. Verify files exist in `dist` directory after build
2. Check if assets are being loaded correctly (browser DevTools → Network tab)

## Rollback to Previous Deployment

Via Dashboard:
1. Go to **Deployments** tab
2. Find the previous working deployment
3. Click **⋯** menu → **Promote to Production**

Via CLI:
```bash
vercel rollback
```

## Additional Resources

- [Vercel Documentation](https://vercel.com/docs)
- [Vite Deployment Guide](https://vitejs.dev/guide/static-deploy.html)
- [Vercel CLI Reference](https://vercel.com/docs/cli)

## Support

For issues specific to:
- **PromptFill**: Open an issue on [GitHub](https://github.com/japen0617/PromptFill/issues)
- **Vercel**: Visit [Vercel Support](https://vercel.com/support)

---

**Made with ❤️ by 角落工作室**
