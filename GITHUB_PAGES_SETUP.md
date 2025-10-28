# Enabling GitHub Pages for Resume Display

This repository now includes a GitHub Pages setup that displays your README, LICENSE, and ganeshk.pdf as tabs on a web interface.

## How to Enable GitHub Pages

1. Go to your repository on GitHub: https://github.com/ganesh-k13/Ganesh-Kathiresan-Resume

2. Click on **Settings** (gear icon in the top navigation)

3. In the left sidebar, click on **Pages** (under "Code and automation")

4. Under "Source", select:
   - Source: **Deploy from a branch**
   - Branch: **main** (or your default branch after merging this PR)
   - Folder: **/ (root)**

5. Click **Save**

6. Wait a few minutes for GitHub to build and deploy your site

7. Your site will be available at: `https://ganesh-k13.github.io/Ganesh-Kathiresan-Resume/`

## Features

The GitHub Pages site includes:

- **README Tab**: Displays your README.md content with formatted markdown
- **LICENSE Tab**: Shows your LICENSE file content
- **Resume (PDF) Tab**: Embeds and displays your ganeshk.pdf file with a download button

## Files Added

- `index.html`: The main page with tabbed interface
- `_config.yml`: GitHub Pages Jekyll configuration
- `GITHUB_PAGES_SETUP.md`: This documentation file

## Customization

You can customize the appearance by editing `index.html`:
- Colors are defined in the `<style>` section
- Tab names can be changed in the navigation buttons
- The layout is responsive and works on mobile devices

## Notes

- The PDF viewer works best in modern browsers (Chrome, Firefox, Safari, Edge)
- If the PDF doesn't display inline, users can still download it using the download button
- The site uses GitHub's dark theme colors for consistency with the GitHub interface
