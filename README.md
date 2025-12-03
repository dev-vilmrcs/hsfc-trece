# SCSS to CSS Compilation Guide

This guide shows you how to compile the `main.scss` file to CSS using different methods.

---

## Method 1: Using VS Code Extension (Easiest)

### Step 1: Install the Extension
1. Open VS Code
2. Go to Extensions (Ctrl+Shift+X)
3. Search for "**Live Sass Compiler**" by Ritwick Dey
4. Click Install

### Step 2: Compile SCSS
1. Open the `main.scss` file in VS Code
2. Look at the bottom right corner of VS Code
3. Click the **"Watch Sass"** button (or "Compile Sass")
4. The compiled `main.css` will automatically appear in the same directory

**Pros:** Very easy, automatic compilation on save  
**Cons:** Requires VS Code extension

---

## Method 2: Using Command Line (Node Sass)

### Step 1: Install Node.js
If you haven't already, download and install [Node.js](https://nodejs.org/) (includes npm)

### Step 2: Install node-sass Globally
Open PowerShell in your project folder and run:
```powershell
npm install -g node-sass
```

### Step 3: Compile Once
To compile a single time:
```powershell
node-sass "c:\Workspace\hsfc-workspace\_Final_na_final\MediLab-1.0.0\MediLab-1.0.0\assets\scss\main.scss" -o "c:\Workspace\hsfc-workspace\_Final_na_final\MediLab-1.0.0\MediLab-1.0.0\assets\css\"
```

Or, shorter version from the folder:
```powershell
node-sass assets/scss/main.scss -o assets/css/
```

### Step 4: Watch for Changes (Auto-Compile)
To automatically compile whenever you save:
```powershell
node-sass assets/scss/main.scss -o assets/css/ --watch
```

**Pros:** Full control, works everywhere, free  
**Cons:** Need to install Node.js and npm

---

## Method 3: Using Dart Sass (Modern & Recommended)

### Step 1: Install Dart Sass Globally
```powershell
npm install -g sass
```

### Step 2: Compile Once
```powershell
sass "c:\Workspace\hsfc-workspace\_Final_na_final\MediLab-1.0.0\MediLab-1.0.0\assets\scss\main.scss" "c:\Workspace\hsfc-workspace\_Final_na_final\MediLab-1.0.0\MediLab-1.0.0\assets\css\main.css"
```

Or from the folder:
```powershell
sass assets/scss/main.scss assets/css/main.css
```

### Step 3: Watch for Changes
```powershell
sass --watch assets/scss:assets/css
```

This watches the entire `scss` folder and outputs to `css` folder.

**Pros:** Modern, maintained by Sass team, excellent performance  
**Cons:** Need to install Node.js

---

## Method 4: Using VS Code Task Runner

### Step 1: Create tasks.json
1. In VS Code, press `Ctrl+Shift+P`
2. Type "Tasks: Configure Task"
3. Select "Create tasks.json from template"
4. Choose "Others"

### Step 2: Add This Task Configuration
Replace the content with:
```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Compile SCSS to CSS",
      "type": "shell",
      "command": "sass",
      "args": [
        "--watch",
        "assets/scss:assets/css"
      ],
      "isBackground": true,
      "presentation": {
        "reveal": "always"
      }
    }
  ]
}
```

### Step 3: Run the Task
1. Press `Ctrl+Shift+P`
2. Type "Tasks: Run Task"
3. Select "Compile SCSS to CSS"
4. SCSS will now auto-compile on save

---

## Method 5: Online SCSS Compiler (No Installation)

If you don't want to install anything:

1. Go to [SassMeister](https://www.sassmeister.com/)
2. Paste your SCSS code
3. Copy the compiled CSS output
4. Paste it into your `main.css` file

**Pros:** No installation needed  
**Cons:** Not ideal for large projects, manual process

---

## Quick Reference Commands

### Using Dart Sass (Recommended)
```powershell
# Install
npm install -g sass

# Compile once
sass input.scss output.css

# Watch folder
sass --watch input-folder:output-folder

# Minified output
sass --style=compressed input.scss output.css
```

### Using Node Sass (Legacy but still works)
```powershell
# Install
npm install -g node-sass

# Compile once
node-sass input.scss -o output-folder/

# Watch folder
node-sass input.scss -o output-folder/ --watch

# Minified output
node-sass input.scss -o output-folder/ --output-style compressed
```

---

## Recommended Setup

**For beginners:** Use **VS Code Live Sass Compiler extension** - it's the easiest!

**For production:** Use **Dart Sass with watch command** - most reliable and modern

---

## How to Update the HTML File

Once you've compiled SCSS to CSS, update your HTML to use the compiled CSS:

### Current (if using main.css)
```html
<link rel="stylesheet" href="assets/css/main.css">
```

### If compiled from SCSS
```html
<link rel="stylesheet" href="assets/css/main.css">
```

The path stays the same - both the CSS and compiled SCSS output to `assets/css/main.css`

---

## Troubleshooting

**Command not found error:**
- Make sure you installed Node.js: https://nodejs.org/
- Close and reopen PowerShell after installing
- Try using full path or reinstall globally

**File not compiling:**
- Check syntax in SCSS file
- Ensure paths are correct
- Try compiling once without watch mode first

**Want minified CSS for production?**
```powershell
sass --style=compressed assets/scss/main.scss assets/css/main.min.css
```
