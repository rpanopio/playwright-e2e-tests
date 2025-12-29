# Playwright Installation

## Steps
1. **Check if Node.js is installed:**
```sh
node -v
```
- Returns a valid node version (e.g. `v22.16.0`). If not, install Node.js first.

2. **Navigate to your project directory:**
```sh
cd /path/to/your/project
```

3. **Initialize Playwright:**
```sh
npm init playwright@latest
```
- When prompted:
  - Select `TypeScript` as the language
  - Choose to install **all browsers**

4. **Verify Playwright installation:**
```sh
npx playwright --version
```
- Shows the installed Playwright version.

---   
#================================================================================#
# Run the Generated Test

## Steps
1. **Run the sample test:**
```sh
npx playwright test --headed
```
- This command runs all Playwright tests in headed mode (browser UI visible).

2. **Show the test report:**
```sh
npx playwright show-report
```
- This command opens the Playwright HTML report for your test run.

---

__Note__: In Windows, If you get an error on running `webkit` browser, add the following config to ignore SSL cert

```ts
use: {
    ignoreHTTPSErrors: true,
  },
```
---

#================================================================================#
## Naming Convention - Best Practice:

### 16.2. File & Code Naming Conventions

| Item                    | Convention                                     | Example                                               |
|-------------------------|------------------------------------------------|-------------------------------------------------------|
| **Folders / Files**     | kebab-case                                     | `page-objects/`, `file-helper.ts`                    |
| **Page and Spec files** | dot-separated                                  | `nopcommerce.home.page.ts`, `nopcommerce.e2e.spec.ts` |
| **Class Names**         | PascalCase (each word capitalized)             | `LoginPage`, `DashboardActions`                       |
| **Variables**           | camelCase                                      | `loginButton`, `userNameInput`                        |
| **Constants**           | UPPER_SNAKE_CASE                               | `BASE_URL`, `API_TIMEOUT_MS`                          |

---

🎯 **Consistent naming improves readability and reduces confusion across teams.**

---

#================================================================================#
# Folder Structure Setup

Let's create the following folder structure:

```sh
PLAYWRIGHT-E2E-TESTS/
├── .github/                    # CI Config folder
├── .vscode/                    # Editor-specific settings
│   └── mcp.json                # MCP server config for VS Code
├── config/                     # Environment-specific config files
├── data/                       # Static data and constants
│   └── constants.json          # Common constants used in tests
├── debug/                      # Optional: Debug-related outputs/logs
├── logs/                       # Application/test logs
├── node_modules/               # Auto-generated dependencies
├── playwright-report/          # Playwright HTML test report output
├── resources/                  # Misc test resources (e.g. images, files)
├── tests/                      # All organized test files
│   ├── api/                    # API test specs
│   ├── demo/                   # Demo-related test specs
│   ├── devices/                # Device related scenarios
│   ├── e2e/                    # End-to-end test specs
│   ├── functional/             # Functional test cases
│   ├── helpers/                # Utility functions for tests
│   ├── page-objects/           # Page Object Model files
├── tests-examples/             # Auto-generated sample test scenarios
├── .env.example                # Template for environment files
├── .env                        # Template for environment files
├── .gitignore                  # Git ignored files and folders
├── package-lock.json           # Dependency lock file
├── package.json                # Project metadata and scripts
├── playwright.config.ts        # Playwright configuration file
├── README.md                   # Project overview and instructions
```

---

## Quick Check

1. In the `playwright.config.ts` file, comment out all other browsers and ensure only `chromium` is enabled.

2. Run the following command to verify everything still works:

```sh
npx playwright test --headed
```

If tests execute successfully, you're all set!

🎯 The target project structure is now set up. Let’s keep moving forward... 🚀

---

#================================================================================#
# Recommended VS Code Extensions

- vscode-icons
- Prettier - Code formatter
- Path Intellisense
- npm Intellisense
- DotENV
- JavaScript (ES6) code snippets
- .gitignore Generator

---

Install these extensions from the VS Code Extensions Marketplace for a smoother and more productive workflow.

#==================================================================================#
# Local Git Setup

1. **Initialize a Local Git repository:**

```sh
git init
```

2. **Check which files are to be staged:**

```sh
git status
```
- This command shows the changes in the current directory.

3. **Add or check project-specific files in the `.gitignore` file.**
   1. You can use the `VS Code` extention to create the content

4. **Stage all files for commit:**

```sh
git add .
```

2. **Check which files are staged or ready to be committed:**

```sh
git status
```

3. **Commit the staged files:**

```sh
git commit -m "Your commit message here"
```
- This command commits all staged changes with a descriptive message.

---
#================================================================================#
1. View available options:
```sh
npx playwright codegen --help
```
2. Run with or without a URL:
```sh
npx playwright codegen
npx playwright codegen https://katalon-demo-cura.herokuapp.com/
```

[💡] __Use CLI for__
- Device emulation
- Custom viewport settings
- Automation scripts and advanced workflows

🎯 **Codegen** can drastically reduce your test writing time and help you learn the best locator strategies along the way.

---

#================================================================================#
# Recommended VS Code Extensions

- vscode-icons
- Prettier - Code formatter
- Path Intellisense
- npm Intellisense
- DotENV
- JavaScript (ES6) code snippets
- .gitignore Generator

---

Install these extensions from the VS Code Extensions Marketplace for a smoother and more productive workflow.
### Option 1: VS Code Extension

1. Open the VS CODE Extensions Marketplace and install:  
   **`Playwright Test for VSCode`**
2. Once installed, look for a new **laboratory flask icon** in the sidebar. Click to open the extension.
3. You can now:
   - **Record tests** interactively
   - **Capture locators** with tooltips and visibility checks

[💡] __Tips While Using the Extension__
- Click on `assertion` tooltips to select an element.
  - `Visibility` checks ensure the element is ready before interacting.
  - `text` selectors provide an extra layer of validation.

---

#================================================================================#
# Button and Link Interactions

## Click Actions
### Methods Used
```js
// Single click on button or link
.click()  

// Double click on button or link
.dblclick()

// Right click on button or link (context menu)
.click({button: 'right'})

// Press Enter key on focused element
.press('Enter')

// Hover over element to show tooltips or trigger hover effects
.hover()

// Click with custom timeout
.click({timeout: 5000})
```

---

## Pro Tips
- ✅ Use `.click()` for most button and link interactions - it's the most reliable method.
- ✅ Use `.press('Enter')` as an alternative to clicking, especially for accessibility testing.
- ✅ Use `.hover()` to trigger hover states before clicking if needed for dropdown menus.
- ✅ Use `.dblclick()` for elements that require double-click activation.
- ✅ Set custom timeouts with `{timeout: 5000}` for slow-loading elements.
- ✅ Right-click with `{button: 'right'}` to test context menus.

---

## Reference 
- Key reference: https://developer.mozilla.org/en-US/docs/Web/API/UI_Events/Keyboard_event_key_values

#======================================================================================# 
Checkbox and Radio Button Interactions

## Check/Uncheck Actions
### Methods Used
```js
// Check a checkbox or radio button
.check()

// Uncheck a checkbox (not applicable to radio buttons)
.uncheck()

// Toggle checkbox state
.setChecked(true)  // Check
.setChecked(false) // Uncheck

// Get inner text content
.innerText()

// Get all elements
.all()
```

---

---

## Pro-tips

- **Radio Button**: Allows selecting only one option from a group
- **Checkbox**: Allows multiple selections (multi-entry)

---
#=======================================================================================#
# Working with Multiple Elements 

## List Iteration and Array Manipulation
### Methods Used
```js
// Use of CSS selector
.locator(".className")

// Count elements
.count()

// Get specific element by index
.nth(index)

// Locator chaining for nested elements
.locator(".parent").locator(".child")

// Get text content
.innerText()
.textContent()

// String manipulation
.trim()
.replace("$", "")

// Array methods
.map()
.filter()
.push()
```

---
#============================================================================#
# Allure Reporter Setup for Playwright

## Installation & Basic Setup

### Step 1: Check and Install Allure Command Line Tool 

```sh
allure --version
```

If you encounter an error like `zsh: command not found: allure`, install the global command line tool:

```sh
npm install -g allure-commandline
```


### Step 1: Install Allure Playwright Package

Install the allure reporter as a development dependency:

```sh
npm install -D allure-playwright
```

---

### Step 2: Configure Reporter in Playwright Config

Update the `reporter` section in your `playwright.config.ts` file:

```ts
reporter: [
  ['html'],                    // Default Playwright HTML reporter
  ['allure-playwright'],       // Allure reporter
],
```

---
Run a test and you will see a folder `allure-results` in the project root

### Step 3: Generate and View Reports

After running your tests, generate the Allure report:

```sh
allure serve
```



## Advanced Configuration

### Enhanced Reporter Setup

For more detailed reporting, you can configure additional options:

```ts
reporter: [
  [
    'html',
    {
      open: 'never', // Don't auto-open HTML report
    },
  ],
  [
    'allure-playwright',
    {
      detail: true,
      suiteTitle: true,
      environmentInfo: {
        name: 'TEST',
        Release: 'Release 1.1',
        node_version: process.version
      },
    },
  ],
],
```

---

### Reference 
- [Allure Advance Config] (https://allurereport.org/docs/playwright/)

--- 

#=======================================================================#
# Java Installation (macOS)

## Steps
1. **Check if Java is installed:**
```sh
java -version
```
- If the version is JDK 8 or higher, skip installation.

2. **Download Java:**
   - Go to [Adoptium Java Downloads](https://adoptium.net/en-GB/)
   - Download the LTS version for macOS

3. **Install:**
   - Run the installer, accept the terms, and complete the installation

4. **Verify installation:**
```sh
java -version
```
   - Shows the installed Java version.

## Notes
- File size: ~180 MB, installation takes a few secondsp

---
