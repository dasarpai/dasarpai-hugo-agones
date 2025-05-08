# Tech Context

## Technologies Used

*   **Static Site Generator:** Hugo
*   **Templating Language:** Go Templating
*   **Content Format:** Markdown
*   **Styling:** CSS (potentially with SASS/SCSS based on `assets/scss/`)
*   **Scripting:** JavaScript (if any)

## Development Setup

*   Hugo executable is required to build and serve the site.
*   Project files are managed in a version control system (likely Git, given the `.gitignore`).
*   Development is currently being done in VS Code.

## Technical Constraints

*   The output is static HTML, CSS, and JavaScript. Dynamic features must be implemented client-side or through external services.
*   Reliance on Hugo's features and capabilities.

## Dependencies

*   Hugo (the executable)
*   Any external libraries or frameworks included in the project (need to investigate further if any are used beyond standard Hugo).

## Tool Usage Patterns

*   Using `hugo server` for local development and previewing changes.
*   Using `hugo` to build the static site for deployment.
*   Utilizing VS Code for editing files.
*   Using Cline (AI Software Engineer) with its available tools (`read_file`, `write_to_file`, `replace_in_file`, `execute_command`, etc.) for development tasks.
