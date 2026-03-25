# GitHub Pages Setup Instructions

This folder contains a GitHub Pages website for the Parameter Estimation Workshop. Follow these steps to publish it:

## Quick Start

### 1. Create a GitHub Repository

1. Go to https://github.com
2. Click the "+" icon → "New repository"
3. Name it something like: `parameter-estimation-workshop`
4. Choose "Public" visibility
5. Do NOT initialize with README (we already have one)
6. Click "Create repository"

### 2. Upload Your Files

**Option A: Using GitHub Web Interface (Easiest)**

1. In your new repository, click "uploading an existing file"
2. Drag all files from this Webpage folder:
   - `_config.yml`
   - `README.md`
   - `day1.md`
   - `day2.md`
   - `day3.md`
   - `phase2-projects.md`
   - `phase2-event.md`
3. Add a commit message: "Initial website commit"
4. Click "Commit changes"

**Option B: Using Git Command Line**

```bash
# Navigate to this Webpage folder
cd "e:\2025-08-13\FGCU\Grants\2025-2026\4-MAA\Webpage"

# Initialize git repository
git init

# Add all files
git add .

# Commit
git commit -m "Initial website commit"

# Connect to GitHub (replace USERNAME and REPO)
git remote add origin https://github.com/USERNAME/REPO.git

# Push to GitHub
git branch -M main
git push -u origin main
```

### 3. Enable GitHub Pages

1. In your repository, go to **Settings** → **Pages** (left sidebar)
2. Under "Source", select:
   - **Branch:** `main`
   - **Folder:** `/ (root)`
3. Click **Save**
4. Wait 1-2 minutes for deployment

### 4. View Your Website

Your site will be available at:
```
https://USERNAME.github.io/REPO-NAME/
```

For example: `https://aacondori.github.io/parameter-estimation-workshop/`

---

## File Structure

```
Webpage/
├── _config.yml              # Jekyll configuration (theme, title)
├── README.md               # Main homepage
├── day1.md                 # Day 1 schedule and details
├── day2.md                 # Day 2 schedule and details
├── day3.md                 # Day 3 schedule and details
├── phase2-projects.md      # Phase Two research topics
├── phase2-event.md         # Symposium event details
└── SETUP.md                # This file
```

---

## Customization

### Change Theme

Edit `_config.yml` and choose from these free themes:
- `jekyll-theme-cayman` (current - colorful headers with gradient)
- `jekyll-theme-minimal` (simple, clean)
- `jekyll-theme-slate` (dark theme)
- `jekyll-theme-architect` (professional)

Full list: https://pages.github.com/themes/

### Contact Information

Contact information (email) has been added throughout the site. Email links use `mailto:` for direct contact.

### Add Images

1. Create an `images/` folder in your repository
2. Upload images (experiment photos, plots, logos)
3. Reference in markdown: `![Description](images/photo.jpg)`

### Tables

All tables use standard Markdown syntax:

```markdown
| Column 1 | Column 2 |
|----------|----------|
| Data 1   | Data 2   |
```

### Math Equations

LaTeX math rendering is already enabled using kramdown and MathJax. You can use math in any markdown file:

**Inline math** (within text):
```markdown
The parameter $k$ controls the cooling rate.
```

**Display math** (centered, on its own line):
```markdown
$$u(t) = A + (u_0 - A)e^{-kt}$$
```

Example with differential equation:
```markdown
$$\frac{du}{dt} = -k(u - A)$$
```

---

## Navigation

The site uses markdown links for navigation:

- `[Text](page.md)` - Links to another page
- `[Text](README.md)` - Links to homepage
- `[Text](#section)` - Links to section on same page

The navigation links are at the bottom of each page (e.g., "← Day 1 | Main | Day 2 →")

---

## Updating Content

**No need to restart the setup process!** Once your site is published, making revisions is simple:

### Method 1: Edit Directly on GitHub (Easiest)
1. Go to your repository on GitHub
2. Click the file you want to edit (e.g., `day1.md`)
3. Click the **✏️ pencil icon** (top right of file view)
4. Make your changes in the editor
5. Scroll down to "Commit changes"
   - Add a brief description (e.g., "Update Day 1 homework")
   - Click **Commit changes**
6. Wait 1-2 minutes—your changes are now live!

### Method 2: Edit Local Files with Git
If you have the files on your computer:

1. **Edit** the files in your text editor (VS Code, Notepad++, etc.)
2. **Add** changes: `git add .` (or specific files like `git add day1.md`)
3. **Commit** with message: `git commit -m "Update homework assignments"`
4. **Push** to GitHub: `git push`
5. Wait 1-2 minutes—changes automatically deploy

### Method 3: Edit Local Files Without Git (Manual Upload)
If you didn't use Git initially:

**Option A: Upload multiple files at once (Recommended for batch changes)**
1. Edit all the files you want on your computer
2. Go to your repository on GitHub
3. Click **"Add file"** → **"Upload files"**
4. Drag and drop all your updated files at once (or click "choose your files")
5. GitHub will automatically replace the old versions with your new ones
6. Add a commit message (e.g., "Update all workshop pages")
7. Click **"Commit changes"**
8. Wait 1-2 minutes—all changes are now live!

**Option B: Update individual files**
1. Edit the file on your computer
2. Go to your repository on GitHub
3. Click the file to replace → **✏️** → Delete all content
4. Copy/paste your updated content
5. Commit changes

### Common Revision Workflows

**Fixing a typo:**
- Use Method 1 (edit directly on GitHub)—fastest for small changes

**Updating multiple files:**
- Use Method 2 (local Git workflow with `git add .` and `git push`)—best for batch changes
- Or Method 3, Option A (upload all files at once)—if not using Git

**Major restructuring:**
- Consider unpublishing first (Settings → Pages → Source: None)
- Make all changes
- Re-enable Pages when ready
- This prevents users seeing half-finished updates

**Testing before publishing:**
- Unfortunately, GitHub Pages doesn't have a "preview" mode
- Best practice: make a test repository first
- Once satisfied, copy changes to your main repository

---

## Unpublishing Your Site

To make your website inaccessible while keeping the repository:

### Option 1: Disable GitHub Pages (Recommended)
1. Go to **Settings** → **Pages**
2. Under "Source", select **None**
3. Click **Save**
4. The site will be taken offline within a few minutes
5. Your files remain in the repository—you can re-enable Pages anytime

### Option 2: Make Repository Private
1. Go to **Settings** → **General**
2. Scroll to "Danger Zone"
3. Click "Change repository visibility" → **Make private**
4. Note: Free GitHub accounts can't use Pages with private repos, so this automatically unpublishes

### Option 3: Delete the Repository
1. Go to **Settings** → **General**
2. Scroll to "Danger Zone"
3. Click "Delete this repository"
4. Type the repository name to confirm
5. **Warning:** This permanently deletes all files and history

**Recommended approach:** Use Option 1 to temporarily unpublish. This preserves your work and allows easy republication by selecting the branch again.

---

## Troubleshooting

**Problem:** Site shows 404 error  
**Solution:** Wait 2-3 minutes after enabling Pages, or check Settings → Pages shows green checkmark

**Problem:** Pages not showing in Settings  
**Solution:** Ensure repository is Public (Pages doesn't work for private repos on free accounts)

**Problem:** Broken links between pages  
**Solution:** Ensure `.md` extension is included in links: `[Day 1](day1.md)` not `[Day 1](day1)`

**Problem:** Theme not loading  
**Solution:** Check `_config.yml` has no syntax errors (YAML is indent-sensitive)

**Problem:** Tables not rendering  
**Solution:** Ensure there's a blank line before and after the table in markdown

---

## Advanced: Custom Domain

If you want to use a custom domain (e.g., `workshop.fgcu.edu`):

1. Add file named `CNAME` (no extension) to repository
2. Content: `workshop.fgcu.edu`
3. Configure DNS with your domain provider:
   - Add CNAME record pointing to `USERNAME.github.io`
4. In Settings → Pages, enter custom domain

---

## Resources

- **GitHub Pages Docs:** https://docs.github.com/en/pages
- **Markdown Guide:** https://www.markdownguide.org/
- **Jekyll Themes:** https://pages.github.com/themes/
- **YAML Syntax:** https://learnxinyminutes.com/docs/yaml/

---

## Questions?

If you encounter issues:
1. Check GitHub Pages build status: Repository → Actions tab
2. Review GitHub Pages documentation
3. Post in GitHub Community: https://github.community/

Happy publishing! 🚀
