# Build Scripts

A build script is a set of automated instructions that prepares your web application for deployment. It performs tasks such as combining files, compressing code, and optimizing images. The script runs inside a build system or task runner.

In a typical web project, you write source code that is easy for humans to read. Browsers, however, benefit from smaller file sizes and fewer requests. A build script bridges this gap. It transforms your development code into production-ready code without manual effort.

Common tasks include:
- Minifying JavaScript and CSS files
- Compiling Sass or Less into standard CSS
- Bundling multiple modules into one file
- Optimizing images
- Running tests before deployment

A complete build script for a small website might include:

1. **Clean** – Remove the old `dist` folder.
2. **Copy assets** – Move HTML and images to `dist`.
3. **Compile CSS** – Convert Sass to CSS and minify.
4. **Bundle JS** – Combine all JavaScript modules into one file and minify.
5. **Watch** – Rerun tasks automatically when source files change during development.

You typically run a build script in three situations:

- **During development** (often automatically via `watch` mode)
- **Before deploying** to a staging or production server
- **In a Continuous Integration (CI) pipeline** (e.g., GitHub Actions, Jenkins)

### Key Terminology

- **Minification**: Removing unnecessary characters from code without changing its function.
- **Bundling**: Combining multiple files into one to reduce HTTP requests.
- **Source map**: A file that maps minified code back to original source code for debugging.
- **Transpilation**: Converting modern JavaScript (ES6+) into older versions for browser compatibility.
- **Hot Module Replacement (HMR)**: Updating modules in a running application without a full refresh.

---

## Example: Writing a Build Script That Converts Markdown To HTML

Assuming we want to convert `src/article.md` from markdown to HTML and have it in the `dist` directory.

+ Create the build script, a file named `scripts/md_to_html.ts`.
+ Write the code to convert the markdown file to HTML and place it in the `dist` directory.
+ Add the build script to `package.json`. Modify the `"scripts"` section.
    ```json
    {
      "name": "markdown-build",
      "version": "1.0.0",
      "scripts": {
        "clean": "rimraf dist",
        "convert:md": "node scripts/md-to-html.js", // Add this line ...
        "prebuild": "npm run clean",
        "build": "npm run convert:md" // ... and this line.
      },
      "devDependencies": {
        "marked": "^11.0.0",
        "fs-extra": "^11.0.0",
        "rimraf": "^5.0.0"
      }
    }
    ```
+ Execute the build script by running `npm run build`.
+ After the build process is done, verify that everything worked as expected.

---

## 9. Best Practices for Build Scripts

- Keep your build script version‑controlled (e.g., in Git).
- Do not commit the `dist/` or `build/` folder to your repository. Add it to `.gitignore`.
- Use environment variables to distinguish between development and production builds.
- Write small, single‑purpose tasks so they are easy to test and reuse.
- Run the build script in a clean environment (like a CI server) to catch missing dependencies.

---
