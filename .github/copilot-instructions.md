# GitHub Copilot Instructions

## Blog (markdown) Conventions

### Post Files
- All blog posts must be placed in `_posts/` directory
- Use filename format: `YYYY-MM-DD-title.md` (e.g., `2025-12-13-my-post.md`)
- Always include YAML front matter at the top of each post

### YAML Front Matter
Required fields:
- `layout: post`
- `title: "Your Post Title"`

Optional but recommended:
- `subtitle: "A brief description"`
- `tags: [tag1, tag2, tag3]`
- `comments: true/false`

### Content Structure
- Use clear heading hierarchy (h2, h3, h4)
- Add blank lines between sections for readability
- Use code blocks with language specification (e.g., ```python, ```javascript)
- Include alt text for all images

### Writing Style
- Write content in English
- Keep paragraphs concise and focused
- Use lists for better readability
- Add relevant tags for post categorization

## Git Commit Guidelines

### Commit Message Format
- Use imperative mood in commit messages (e.g., "Add feature" not "Added feature")
- Start with a verb: Add, Update, Fix, Remove, Refactor, etc.
- Keep the summary line under 50 characters
- Use present tense

### Commit Message Structure
```
<type>: <short summary>

<detailed description (optional)>
```

### Types
- `feat`: New feature or content
- `fix`: Bug fix or correction
- `docs`: Documentation changes
- `style`: Formatting, CSS changes (no code change)
- `refactor`: Code refactoring
- `chore`: Maintenance tasks

### Examples
Good commit messages:
- `feat: Add atomic habits book review post`
- `fix: Correct typo in classification metrics post`
- `style: Update post layout spacing`
- `docs: Update README with setup instructions`

### Description Guidelines
- Explain WHAT changed and WHY (not HOW)
- Use bullet points for multiple changes
- Reference issue numbers if applicable
- Keep it concise but informative
