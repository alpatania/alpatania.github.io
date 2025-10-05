# What to Edit vs. Never Touch - Your Jekyll Site Guide

## 🎯 The Golden Rule

**90% of your updates happen in just 4 places:**
1. `_pages/` - Your main content pages
2. `_publications/` - Your papers
3. `_talks/` - Your presentations
4. `_data/navigation.yml` - Your menu

Everything else is "plumbing" that makes the site work!

---

## ✏️ FILES YOU'LL EDIT REGULARLY

### 1. Content Pages - `_pages/`
**What's here:** Your main website pages
**Edit these often!**

```
_pages/
├── about.md          ✏️ EDIT - Your homepage/bio
├── publications.md   ✏️ EDIT - Publications page intro
├── code.md          ✏️ EDIT - Code projects page
├── talks.md         ✏️ EDIT - Talks page intro
├── teaching.md      ✏️ EDIT - Teaching page intro
└── cv.md            ✏️ EDIT - Your CV content
```

**How to edit:** Open in any text editor, write in Markdown
**When to edit:** Updating your bio, changing page content
**Example:**
```markdown
---
layout: archive
title: "Publications"
permalink: /publications/
---

Here are my research publications...
```

### 2. Individual Publications - `_publications/`
**What's here:** Each paper as a separate file
**Edit these when adding/updating papers!**

```
_publications/
├── 2021-02-23-nerve.md    ✏️ EDIT - Update paper details
└── [add new papers here]  ✏️ CREATE - New publications
```

**When to edit:** New paper published, fixing a link, updating citation
**Example:**
```markdown
---
title: "Your Paper Title"
collection: publications
permalink: /publication/2021-nerve
date: 2021-02-23
venue: 'Journal Name'
paperurl: 'http://link-to-paper.com'
---
```

### 3. Individual Talks - `_talks/`
**What's here:** Each talk/poster as a separate file
**Edit these when adding talks!**

```
_talks/
├── 2024-06-17-talk.md     ✏️ EDIT - Update talk details
└── [add new talks here]   ✏️ CREATE - New presentations
```

### 4. Site Navigation - `_data/navigation.yml`
**What's here:** Your top menu
**Edit when adding/removing menu items!**

```yaml
main:
  - title: "Publications"
    url: /publications/
  - title: "Code"
    url: /code/
  # Add new menu items here
```

**When to edit:** Adding a new page to menu, reordering menu items

### 5. Site Configuration - `_config.yml`
**What's here:** Site-wide settings
**Edit occasionally**

```yaml
# Site Settings
title: "Alice Patania"
name: "Alice Patania"
description: "Computational Topologist"
url: "https://alpatania.github.io"

# Social media links
twitter_username: YourHandle
github_username: alpatania
```

**When to edit:** 
- Changing site title
- Updating social media links
- Changing author info in sidebar

### 6. Styling Variables - `_sass/_variables.scss`
**What's here:** Colors, fonts, spacing
**Edit when customizing design**

```scss
/* Colors */
$link-color: #0066cc;
$text-color: #333;

/* Fonts */
$sans-serif: "Helvetica", Arial, sans-serif;
```

**When to edit:** Changing site colors, fonts, or basic styling

---

## 🚫 FILES YOU SHOULD NEVER TOUCH

### 1. Theme Includes - `_includes/`
**What's here:** HTML templates that build your pages
**DON'T edit these unless you're advanced!**

```
_includes/
├── head.html              🚫 NEVER - HTML <head> generation
├── footer.html            🚫 NEVER - Footer generation
├── masthead.html          🚫 NEVER - Top navigation
├── sidebar.html           🚫 NEVER - Sidebar generation
├── archive-single.html    🚫 NEVER - Item formatting
├── seo.html               🚫 NEVER - SEO metadata
├── scripts.html           🚫 NEVER - JavaScript loading
└── [most other files]     🚫 NEVER - Technical templates
```

**Why not:** These are complex templates. Editing them can break your site.
**Exception:** `_includes/footer/custom.html` and `_includes/head/custom.html` are SAFE to edit

### 2. Layout Templates - `_layouts/`
**What's here:** Page structure templates
**DON'T touch!**

```
_layouts/
├── default.html       🚫 NEVER - Base page structure
├── single.html        🚫 NEVER - Single page layout
├── archive.html       🚫 NEVER - Collection pages layout
└── [all others]       🚫 NEVER - Technical layouts
```

**Why not:** These control how pages are built. Breaking them affects everything.

### 3. Sass Partials - `_sass/vendor/`
**What's here:** Third-party CSS libraries
**DON'T touch!**

```
_sass/vendor/
├── breakpoint/        🚫 NEVER - Responsive design library
├── font-awesome/      🚫 NEVER - Icon fonts
├── magnific-popup/    🚫 NEVER - Popup library
└── susy/              🚫 NEVER - Grid system
```

**Why not:** These are external libraries. You'll break things.

### 4. JavaScript Files - `assets/js/`
**What's here:** Site functionality
**DON'T edit unless you know JavaScript!**

```
assets/js/
├── main.min.js        🚫 NEVER - Minified site JavaScript
├── _main.js           🚫 RARELY - Source JavaScript
└── plugins/           🚫 NEVER - jQuery plugins
```

### 5. Jekyll Configuration Files
**What's here:** Ruby/Jekyll dependencies
**DON'T touch!**

```
Gemfile           🚫 NEVER (unless updating Jekyll)
Gemfile.lock      🚫 NEVER (auto-generated)
package.json      🚫 NEVER (dependencies)
```

---

## ⚠️ EDIT WITH CAUTION

### Files you might edit, but be careful:

#### 1. `_sass/michele.scss` or custom SCSS files
**What's here:** Custom styling
**Edit carefully:** Only if you know CSS/SCSS

#### 2. `_includes/author-profile.html`
**What's here:** Your sidebar profile
**Edit if:** Customizing sidebar beyond _config.yml settings

#### 3. `_includes/footer/custom.html`
**What's here:** Custom footer content
**Safe to edit:** Add copyright, extra links, etc.

#### 4. `_includes/head/custom.html`
**What's here:** Custom HTML head additions
**Safe to edit:** Add custom fonts, meta tags, etc.

---

## 🎓 Common Update Scenarios

### Scenario 1: "I published a new paper"
**What to do:**
1. Create new file in `_publications/`
2. Copy format from existing publication
3. Update title, date, venue, link
4. Commit and push

**Files touched:** 1 (new .md file in `_publications/`)

### Scenario 2: "I want to update my bio"
**What to do:**
1. Edit `_pages/about.md`
2. Write in Markdown
3. Commit and push

**Files touched:** 1 (`_pages/about.md`)

### Scenario 3: "I want to add a new section to my site"
**What to do:**
1. Create new file in `_pages/` (e.g., `research.md`)
2. Add entry to `_data/navigation.yml`
3. Commit and push

**Files touched:** 2 (new page + navigation)

### Scenario 4: "I want to change my site colors"
**What to do:**
1. Edit `_sass/_variables.scss`
2. Change color hex codes
3. Test locally, then push

**Files touched:** 1 (`_sass/_variables.scss`)

### Scenario 5: "I gave a talk at a conference"
**What to do:**
1. Create new file in `_talks/`
2. Copy format from existing talk
3. Update details
4. Commit and push

**Files touched:** 1 (new .md file in `_talks/`)

---

## 📁 Your Editing Workflow

### Daily/Weekly Updates (90% of your work):
```
You edit:
├── _pages/           ← Content updates
├── _publications/    ← New papers
├── _talks/           ← New presentations
├── _teaching/        ← Course updates
└── _code/            ← Project updates
```

### Monthly/Rare Updates (9% of your work):
```
You edit:
├── _config.yml              ← Site settings
├── _data/navigation.yml     ← Menu changes
├── files/                   ← Upload new PDFs
└── images/                  ← Upload new images
```

### Almost Never (1% of your work):
```
You edit:
├── _sass/_variables.scss    ← Design changes
├── _includes/footer/custom.html
└── _includes/head/custom.html
```

### NEVER TOUCH:
```
Don't edit:
├── _includes/      (except custom.html files)
├── _layouts/
├── _sass/vendor/
├── assets/js/
├── Gemfile
└── Gemfile.lock
```

---

## 🎯 Quick Reference Card

**Print this out and keep it handy!**

| Task | Edit This | Never Touch |
|------|-----------|-------------|
| Update bio | `_pages/about.md` | `_includes/author-profile.html` |
| New paper | Create in `_publications/` | `_includes/archive-single.html` |
| New talk | Create in `_talks/` | `_layouts/talk.html` |
| Change menu | `_data/navigation.yml` | `_includes/masthead.html` |
| Site colors | `_sass/_variables.scss` | `_sass/vendor/` |
| Social links | `_config.yml` | `_includes/footer.html` |
| Upload PDF | Drop in `files/` | Don't touch `assets/` |

---

## 💡 Pro Tips

### 1. **Use the "Copy and Modify" approach**
When adding a new publication/talk, don't start from scratch:
```bash
# Copy existing file
cp _publications/2021-02-23-nerve.md _publications/2025-01-15-new-paper.md
# Edit the copy with your new info
```

### 2. **Test locally before pushing**
```bash
bundle exec jekyll serve
# Visit localhost:4000 to preview
```

### 3. **Understand the front matter**
Every content file starts with "front matter" between `---`:
```markdown
---
title: "Your Title"
collection: publications
date: 2025-01-15
---

Content goes here...
```
This tells Jekyll how to process the file.

### 4. **When in doubt, don't edit it**
If a file looks technical and you're unsure, don't edit it! Stick to the content files in `_pages/`, `_publications/`, and `_talks/`.

### 5. **Make backups before experimenting**
```bash
# Create a branch before making changes
git checkout -b experiment
# Make your changes
# If it breaks, go back
git checkout main
```

---

## 🆘 "I Broke Something!" Recovery

### If your site breaks after an edit:

1. **Check what you changed:**
   ```bash
   git status
   git diff
   ```

2. **Undo recent changes:**
   ```bash
   git checkout -- filename.md
   ```

3. **Go back to last working version:**
   ```bash
   git reset --hard HEAD
   ```

4. **Check Jekyll build errors:**
   ```bash
   bundle exec jekyll serve
   # Read the error message
   ```

---

## 📚 Summary

**Your typical workflow:**
1. ✏️ Edit content files in `_pages/`, `_publications/`, `_talks/`
2. ✏️ Occasionally update `_data/navigation.yml` or `_config.yml`
3. 🚫 Never touch `_includes/`, `_layouts/`, `_sass/vendor/`, `assets/js/`

**Remember:**
- Content = Easy to edit (Markdown files)
- Theme/Structure = Don't touch (HTML templates)
- Configuration = Edit carefully (YAML files)
- Styling = Edit rarely (_sass/ files)

## To run locally (not on GitHub Pages, to serve on your own computer)
1. Clone the repository and made updates as detailed above
1. Make sure you have ruby-dev, bundler, and nodejs installed: `sudo apt install ruby-dev ruby-bundler nodejs`
1. Run `bundle clean` to clean up the directory (no need to run `--force`)
1. Run `bundle install` to install ruby dependencies. If you get errors, delete Gemfile.lock and try again.
1. Run `bundle exec jekyll serve` to generate the HTML and serve it from localhost:4000
