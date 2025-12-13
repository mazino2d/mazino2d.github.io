# Mazino Space

Personal blog and portfolio website built with Jekyll and Beautiful Jekyll theme, hosted on GitHub Pages.

## About

This is my personal space on the internet where I share insights and write about topics that interest me, including:

- 💰 Money & Finance
- ✈️ Travel
- 🗣️ English
- 💻 Code & Technology
- 📚 Book Summaries

Visit the live site at: [https://mazino2d.github.io](https://mazino2d.github.io)

## Features

- Clean and responsive design using Beautiful Jekyll theme
- Blog posts with tags and categories
- About me page
- Social media integration
- Comment system support (Disqus, Giscus, Utterances)
- Google Analytics integration
- SEO optimized

## Technology Stack

- **Jekyll**: Static site generator
- **Beautiful Jekyll**: Theme template
- **GitHub Pages**: Hosting platform
- **Markdown**: Content writing
- **HTML/CSS/JavaScript**: Frontend

## Local Development

### Prerequisites

- Ruby (2.5.0 or higher)
- RubyGems
- Bundler
- Jekyll

### Compilation Setup

1. Clone the repository:

   ```bash
   git clone https://github.com/mazino2d/mazino2d.github.io.git
   cd mazino2d.github.io
   ```

2. Install dependencies:

   ```bash
   bundle install
   ```

3. Run the local server:

   ```bash
   bundle exec jekyll serve
   ```

4. Open your browser and navigate to:

   ```plaintext
   http://localhost:4000
   ```

The site will automatically rebuild when you make changes to the source files.

## Pre-commit Setup (Optional)

This project uses pre-commit hooks to automatically check code quality before each commit.

### What Pre-commit Checks

- **Markdown Linting**: Uses `markdownlint-cli2` (Node.js) to enforce Markdown style guidelines
- **YAML Linting**: Uses `yamllint` (Conda) to validate YAML syntax and formatting

### Installing Pre-commit

1. Install pre-commit:

   ```bash
   # macOS
   brew install pre-commit

   # or using pip
   pip install pre-commit
   ```

2. Install the git hook scripts:

   ```bash
   pre-commit install
   ```

3. Pre-commit will automatically create isolated environments and install dependencies:

   - Node.js environment for `markdownlint-cli2`
   - Conda environment for `yamllint`

   The first run will take time to set up these environments.

### Running Pre-commit Manually

To run pre-commit hooks on all files manually:

```bash
pre-commit run --all-files
```

To run pre-commit on specific files:

```bash
pre-commit run --files path/to/file.md
```

To run a specific hook:

```bash
# Lint Markdown only
pre-commit run lint-markdown --all-files

# Lint YAML only
pre-commit run lint-yaml --all-files
```

### Pre-commit Configuration

The pre-commit configuration is in `.pre-commit-config.yaml`:

- **lint-markdown**: Checks all `.md` files using markdownlint-cli2 (runs in Node.js environment)
- **lint-yaml**: Checks all `.yaml` and `.yml` files using yamllint (runs in Conda environment)

Both tools run in isolated environments managed by pre-commit, so you don't need to install them manually.

### Troubleshooting

If pre-commit fails:

1. Review the error messages
2. Fix the issues in your files
3. Stage the fixes: `git add .`
4. Try committing again

To skip pre-commit hooks (not recommended):

```bash
git commit --no-verify
```

## Project Structure

```plaintext
.
├── _config.yml           # Site configuration
├── _posts/               # Blog posts
├── _layouts/             # Page layouts
├── _includes/            # Reusable components
├── _data/                # Data files
├── assets/               # Static assets (CSS, JS, images)
├── aboutme.md            # About page
├── tags.html             # Tags page
└── index.html            # Homepage
```

## Writing a New Post

1. Create a new Markdown file in the `_posts` directory with the naming format:

   ```plaintext
   YYYY-MM-DD-title.md
   ```

2. Add front matter at the top of the file:

   ```yaml
   ---
   layout: post
   title: Your Post Title
   subtitle: Optional subtitle
   tags: [tag1, tag2]
   comments: true
   ---
   ```

3. Write your content in Markdown below the front matter.

4. Commit and push to GitHub. The site will automatically rebuild.

## Configuration

Edit `_config.yml` to customize:

- Site title and description
- Author information
- Navigation links
- Social media links
- Analytics tracking
- Comment system settings

## License

This project uses the Beautiful Jekyll theme. See [LICENSE](LICENSE) for details.

## Contact

- **Email**: <mazino2d@gmail.com>
- **GitHub**: [@mazino2d](https://github.com/mazino2d)

## Acknowledgments

- [Beautiful Jekyll](https://beautifuljekyll.com/) - Theme by Dean Attali
- [GitHub Pages](https://pages.github.com/) - Hosting platform
- [Jekyll](https://jekyllrb.com/) - Static site generator
