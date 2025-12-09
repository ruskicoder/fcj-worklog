# GitHub Pages Deployment Fix

## Issues Fixed

1. ✅ Updated `baseURL` in `config.toml` to correct GitHub Pages URL
2. ✅ Removed conflicting `--baseURL` flag from GitHub Actions workflow
3. ✅ Verified Hugo theme is properly installed
4. ✅ Confirmed Hugo builds successfully locally

## GitHub Repository Settings Required

To complete the deployment, you need to configure GitHub Pages in your repository:

### Step 1: Enable GitHub Pages

1. Go to your repository: https://github.com/ruskicoder/fcj-worklog
2. Click on **Settings** tab
3. Scroll down to **Pages** section (left sidebar)
4. Under **Source**, select:
   - **Source**: GitHub Actions (NOT "Deploy from a branch")
   
   This is CRITICAL - you must select "GitHub Actions" as the source!

### Step 2: Commit and Push Changes

```bash
git add config.toml .github/workflows/hugo.yml
git commit -m "Fix GitHub Pages deployment configuration"
git push origin main
```

### Step 3: Monitor Deployment

1. Go to the **Actions** tab in your repository
2. You should see a workflow run starting automatically
3. Wait for it to complete (usually 1-2 minutes)
4. Once successful, your site will be available at:
   **https://ruskicoder.github.io/fcj-worklog/**

## Troubleshooting

### If the workflow fails:

1. **Check the Actions tab** for error messages
2. **Verify GitHub Pages is set to "GitHub Actions"** (not "Deploy from a branch")
3. **Ensure the workflow has proper permissions**:
   - Go to Settings > Actions > General
   - Under "Workflow permissions", select "Read and write permissions"
   - Check "Allow GitHub Actions to create and approve pull requests"

### If you see 404 errors:

1. Wait 5-10 minutes after first deployment
2. Clear your browser cache
3. Try accessing: https://ruskicoder.github.io/fcj-worklog/

### If CSS/images don't load:

1. Verify `baseURL` in `config.toml` matches your GitHub Pages URL exactly
2. Check that `relativeURLs = false` and `canonifyURLs = false`

## What Changed

### config.toml
```toml
# Before:
baseURL = "/"
relativeURLs = true
canonifyURLs = true

# After:
baseURL = "https://ruskicoder.github.io/fcj-worklog/"
relativeURLs = false
canonifyURLs = false
```

### .github/workflows/hugo.yml
Removed the `--baseURL` flag from the build command to use the config.toml value instead.

## Next Steps

1. ✅ Commit and push the changes
2. ✅ Configure GitHub Pages settings (Source: GitHub Actions)
3. ✅ Wait for workflow to complete
4. ✅ Visit your site at https://ruskicoder.github.io/fcj-worklog/

Your site should now deploy successfully! 🚀
