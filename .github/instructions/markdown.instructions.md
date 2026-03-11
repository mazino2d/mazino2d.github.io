---
applyTo: "**/*.md"
---

# Markdown Files Instructions

## Post Files

- All blog posts must be placed in `_posts/` directory
- Use filename format: `YYYY-MM-DD-title.md` (e.g., `2025-12-13-my-post.md`)
- Always include YAML front matter at the top of each post

## YAML Front Matter

Required fields:

- `layout: post`
- `title: "Your Post Title"`

Optional but recommended:

- `subtitle: "A brief description"`
- `tags: [tag1, tag2, tag3]`
- `comments: true/false`

## Series Configuration

For posts that belong to a series, add these front matter fields:

- `series: "Series Name"`
- `series_part: 1` (use sequential numbers: 1, 2, 3...)

Series rules:

- Use the same `series` value across all posts in the same series
- Ensure each post in a series has a unique `series_part`
- Keep `series_part` numeric so navigation order is correct

Example:

```yaml
---
layout: post
title: "My Series Post"
series: "Machine Learning Basics"
series_part: 2
---
```

## Content Structure

- Use clear heading hierarchy (h2, h3, h4)
- Add blank lines between sections for readability
- Use code blocks with language specification (e.g., ```python,```javascript)
- Include alt text for all images

## Writing Style

- Write content in English
- Keep paragraphs concise and focused
- Use lists for better readability
- Add relevant tags for post categorization
