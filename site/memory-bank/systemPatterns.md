# System Patterns

## Architecture

This project follows a standard Hugo static site generation architecture. Content is written in Markdown, and layouts are defined using HTML templates with Go templating.

## Key Technical Decisions

*   Using Hugo for fast static site generation.
*   Organizing layouts by section for customization.
*   Utilizing Hugo's built-in features where possible (e.g., `.TableOfContents`).

## Design Patterns

*   **Templating:** Using Hugo's Go templating for dynamic content generation within static files.
*   **Partial Templates:** Breaking down layouts into smaller, reusable partials (e.g., `header`, `footer`, `sidebar`).

## Component Relationships

*   Content files (`.md`) are processed by Hugo using the appropriate layout files based on their section and type.
*   Layout files (`.html`) include partials for common elements.
*   CSS and JavaScript assets are typically linked in the `head` or before the closing `body` tag in the base layout.
