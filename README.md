# FCJ Workshop Template - Hugo Internship Worklog

A comprehensive Hugo template for creating professional internship worklog websites. This template is designed specifically for AWS internship programs but can be adapted for any technical internship documentation.

## ✨ Features

- **Bilingual Support** - Complete English and Vietnamese content structure
- **Professional Layout** - Clean, organized presentation suitable for internship documentation
- **Multiple Sections** - Worklog, blog translations, workshops, events, self-evaluation, and feedback
- **Responsive Design** - Mobile-friendly with the hugo-theme-learn theme
- **Easy Customization** - Simple content replacement workflow
- **Static Site Generation** - Fast, secure, and easy to deploy

## 🚀 Quick Start

### Prerequisites

You'll need Hugo installed on your system. If you don't have it:

**Windows:**

```bash
# Using Chocolatey
choco install hugo-extended

# Or download from https://github.com/gohugoio/hugo/releases
```

**macOS:**

```bash
# Using Homebrew
brew install hugo
```

**Linux:**

```bash
# Using snap
sudo snap install hugo

# Or download from https://github.com/gohugoio/hugo/releases
```

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/YOUR_USERNAME/fcj-workshop-template-main.git
   cd fcj-workshop-template-main
   ```

2. **Initialize the theme submodule**

   ```bash
   git submodule update --init --recursive
   ```

3. **Run the development server**

   ```bash
   hugo server
   ```

4. **View your site**
   Open your browser and go to `http://localhost:1313/workshop-template/`

5. **Share your local site (Optional)**

   If you want to share your localhost with others for quick preview:

   **Using VS Code Port Forwarding:**
   - In VS Code, open the "Ports" panel (View > Ports or Ctrl+`)
   - Click "Forward a Port" and enter `1313`
   - Set visibility to "Public"
   - Copy the forwarded address (e.g., `https://xyz-1313.preview.app.github.dev`)
   - Share this link with others for temporary access

   **Using ngrok:**

   ```bash
   # Install ngrok from https://ngrok.com/download
   ngrok http 1313
   ```

   Share the URL with `/workshop-template/` appended: `https://abc123.ngrok.io/workshop-template/`

   **Note:** These forwarding methods are temporary and only work while your local server is running.

## 📝 Customization Guide

### Step 1: Update Personal Information

Edit the main index files with your information:

**English Version** (`content/_index.md`):

```markdown
### Student Information:
&emsp; **Full Name:** Your Full Name
&emsp; **Phone Number:** Your Phone
&emsp; **Email:** your.email@example.com
&emsp; **University:** Your University
&emsp; **Major:** Your Major
&emsp; **Class:** Your Class
&emsp; **Internship Company:** Company Name
&emsp; **Internship Position:** Your Position
&emsp; **Internship Duration:** Start Date to End Date
```

**Vietnamese Version** (`content/_index.vi.md`):

```markdown
### Thông tin sinh viên:
&emsp; **Họ và tên:** Tên đầy đủ của bạn
&emsp; **Số điện thoại:** Số điện thoại
&emsp; **Email:** email.cua.ban@example.com
# ... (similar pattern)
```

**Site Configuration** (`config.toml`):

```toml
author = "your.email@example.com"
```

### Step 2: Update Weekly Worklog

Navigate to `content/1-Worklog/1.X-WeekX/` folders and update:

- `_index.md` - English content
- `_index.vi.md` - Vietnamese content

Replace template content with your actual weekly activities, learnings, and achievements.

### Step 3: Update Blog Translations

In `content/3-BlogsTranslated/3.X-BlogX/` folders:

- Add your actual blog translation work
- Update titles and descriptions
- Maintain the same file structure

### Step 4: Customize Other Sections

- **Workshops** (`content/5-Workshop/`): Update with actual workshop participation
- **Events** (`content/4-EventParticipated/`): Document events you attended  
- **Self-Evaluation** (`content/6-Self-evaluation/`): Write your honest assessment
- **Feedback** (`content/7-Feedback/`): Include feedback received

### Step 5: Replace Profile Picture

Replace `static/images/avatar.png` with your own photo (keep the same filename).

## 📁 Folder Structure

```
content/
├── _index.md & _index.vi.md           # Main landing page (EN/VI)
├── 1-Worklog/                         # Weekly internship activities
│   ├── _index.md & _index.vi.md      # Worklog overview
│   ├── 1.1-Week1/                    # Individual week folders
│   └── ...
├── 2-Proposal/                        # Internship proposals
├── 3-BlogsTranslated/                 # Blog translation work
│   ├── 3.1-Blog1/                    # Individual blog folders
│   └── ...
├── 4-EventParticipated/               # Events attended
├── 5-Workshop/                        # Workshop documentation
├── 6-Self-evaluation/                 # Personal assessment
└── 7-Feedback/                        # Feedback collection
```

### Adjusting the Structure

**To add more weeks:**

1. Copy an existing week folder (e.g., `1.1-Week1/`)
2. Rename it (e.g., `1.13-Week13/`)
3. Update the front matter `weight` and `pre` values
4. Update parent index files to include new week

**To remove sections:**

1. Delete the unwanted folder
2. Remove references from main index files
3. Update navigation weights if needed

## 🔧 Development Workflow

### Local Development

1. **Start development server**

   ```bash
   hugo server -D
   ```

   The `-D` flag includes draft content.

2. **Make your changes**
   Edit markdown files in the `content/` directory.

3. **Preview changes**
   Changes auto-reload at `http://localhost:1313`

4. **Build for production**

   ```bash
   hugo
   ```

   This generates the `public/` folder with your static site.

### Content Updates

- **Daily updates**: Edit the current week's markdown files
- **New entries**: Create new folders following the naming convention
- **Images**: Add to `static/images/` and reference as `/images/filename.png`
- **Bilingual content**: Always update both `_index.md` and `_index.vi.md`

## 🌐 Deployment

### GitHub Pages

1. **Create GitHub repository** (if not already done)

2. **Update config.toml**

   ```toml
   baseURL = "https://yourusername.github.io/repository-name/"
   ```

3. **Create GitHub Actions workflow** (`.github/workflows/hugo.yml`):

   ```yaml
   name: Deploy Hugo site to Pages
   
   on:
     push:
       branches: ["main"]
   
   jobs:
     build:
       runs-on: ubuntu-latest
       steps:
         - uses: actions/checkout@v4
           with:
             submodules: recursive
         - name: Setup Hugo
           uses: peaceiris/actions-hugo@v2
           with:
             hugo-version: 'latest'
             extended: true
         - name: Build
           run: hugo --minify
         - name: Deploy
           uses: peaceiris/actions-gh-pages@v3
           with:
             github_token: ${{ secrets.GITHUB_TOKEN }}
             publish_dir: ./public
   ```

4. **Enable Pages in repository settings**
   - Go to Settings > Pages
   - Select "Deploy from a branch"
   - Choose `gh-pages` branch

### Amazon S3 Static Website

1. **Build your site**

   ```bash
   hugo --minify
   ```

2. **Create S3 bucket**

   ```bash
   aws s3 mb s3://your-website-bucket-name
   ```

3. **Configure bucket for static website hosting**

   ```bash
   aws s3 website s3://your-website-bucket-name --index-document index.html --error-document 404.html
   ```

4. **Upload files**

   ```bash
   aws s3 sync public/ s3://your-website-bucket-name --delete
   ```

5. **Set bucket policy for public access**

   ```json
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Sid": "PublicReadGetObject",
         "Effect": "Allow",
         "Principal": "*",
         "Action": "s3:GetObject",
         "Resource": "arn:aws:s3:::your-website-bucket-name/*"
       }
     ]
   }
   ```

6. **Access your website**
   Your site will be available at: `http://your-website-bucket-name.s3-website-[region].amazonaws.com`

## 🛠️ Troubleshooting

**Hugo build errors:**

- Check your markdown front matter syntax
- Ensure all internal links are correct
- Verify image paths start with `/`

**Theme issues:**

- Run `git submodule update --init --recursive`
- Check that the theme folder exists in `themes/hugo-theme-learn/`

**Deployment issues:**

- Verify your `baseURL` in `config.toml`
- Check that the `public/` folder contains your built site
- Ensure proper permissions for S3 bucket or GitHub Pages

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Credits

- **Template created by:** [ruskicoder](https://github.com/ruskicoder)
- **Original inspiration:** FCJ (First Cloud Journey) team
- **Theme:** [hugo-theme-learn](https://github.com/matcornic/hugo-theme-learn)

## 📞 Support

If you encounter any issues or have questions about using this template, please open an issue on GitHub or refer to the [Hugo documentation](https://gohugo.io/documentation/).

---

**Happy documenting your internship journey! 🚀**
