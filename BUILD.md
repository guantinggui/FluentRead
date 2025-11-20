# Building and Installing FluentRead

This guide explains how to build the FluentRead browser extension from source and install it in your browser.

## Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (version 16 or higher) - [Download here](https://nodejs.org/)
- **pnpm** (package manager) - Install via: `npm install -g pnpm`

Check your versions:
```bash
node --version  # Should be v16.0.0 or higher
pnpm --version  # Should be 7.0.0 or higher
```

## Getting Started

1. **Clone the repository**
   ```bash
   git clone https://github.com/Bistutu/FluentRead.git
   cd FluentRead
   ```

2. **Install dependencies**
   ```bash
   pnpm install
   ```

   This will install all required packages and prepare the WXT development environment.

## Building the Extension

### For Chrome/Edge (Chromium-based browsers)

```bash
pnpm run build
```

The built extension will be in `.output/chrome-mv3/`

### For Firefox

```bash
pnpm run build:firefox
```

The built extension will be in `.output/firefox-mv2/`

## Installing the Extension

### Chrome / Edge / Chromium-based Browsers

1. Open your browser and navigate to:
   - **Chrome**: `chrome://extensions/`
   - **Edge**: `edge://extensions/`
   - **Brave**: `brave://extensions/`

2. Enable **Developer mode** (toggle in the top-right corner)

3. Click **Load unpacked**

4. Navigate to your FluentRead directory and select:
   - `.output/chrome-mv3/` folder

5. The extension should now be loaded and active!

### Firefox

1. Open Firefox and navigate to: `about:debugging#/runtime/this-firefox`

2. Click **Load Temporary Add-on...**

3. Navigate to your FluentRead directory and select:
   - `.output/firefox-mv2/manifest.json` file

4. The extension will be loaded temporarily (until you close Firefox)

**Note**: For permanent installation in Firefox, you need to sign the extension through [AMO (addons.mozilla.org)](https://addons.mozilla.org/).

## Development Mode

For development with hot-reload:

### Chrome/Edge
```bash
pnpm run dev
```

### Firefox
```bash
pnpm run dev:firefox
```

This will start a development server that automatically reloads when you make changes to the code.

## Creating Distribution Packages

To create ZIP files for distribution:

### Chrome/Edge
```bash
pnpm run zip
```

Output: `.output/chrome-mv3-{version}.zip`

### Firefox
```bash
pnpm run zip:firefox
```

Output: `.output/firefox-mv2-{version}.zip`

These ZIP files can be submitted to browser extension stores.

## Project Structure

```
FluentRead/
├── components/          # Vue components
├── entrypoints/        # Extension entry points (background, content scripts, popup)
├── public/             # Static assets (icons, images)
├── styles/             # Global styles
├── docs/               # Documentation (VitePress)
├── .output/            # Build output (generated)
│   ├── chrome-mv3/     # Chrome build
│   └── firefox-mv2/    # Firefox build
├── package.json        # Dependencies and scripts
├── wxt.config.ts       # WXT configuration
└── tsconfig.json       # TypeScript configuration
```

## Common Issues

### `pnpm: command not found`
Install pnpm globally:
```bash
npm install -g pnpm
```

### Build fails with TypeScript errors
Try cleaning and reinstalling:
```bash
rm -rf node_modules .wxt
pnpm install
pnpm run build
```

### Extension doesn't load in browser
- Make sure you selected the correct folder (`.output/chrome-mv3/` or `.output/firefox-mv2/`)
- Check browser console for error messages
- Try rebuilding: `pnpm run build` or `pnpm run build:firefox`

## Additional Scripts

- `pnpm run compile` - Type-check TypeScript without building
- `pnpm run docs:dev` - Start documentation development server
- `pnpm run docs:build` - Build documentation site

## Resources

- [Official Documentation](https://fluent.thinkstu.com/)
- [WXT Documentation](https://wxt.dev/)
- [Chrome Extension Development Guide](https://developer.chrome.com/docs/extensions/)
- [Firefox Extension Development Guide](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions)

## License

This project is licensed under the terms specified in the LICENSE file.
