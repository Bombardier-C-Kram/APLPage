# APLPage

A minimal templating library for Dyalog APL that renders `.aplp` pages by substituting placeholder markers with values from a supplied APL namespace.

---

## Features
- Load and parse `.aplp` template files containing HTML or text
- Placeholder syntax: `<!--⋄ VariableName ⋄-->`
- Substitute markers with variables from a provided namespace (ctx)
- No external dependencies required
- [Packaged](https://tatin.dev/v1/packages/major_versions/bkaw-APLPage) for Tatin package manager

## Installation

### Via Tatin (APL package manager)
1. Add `APLPage` to your `apl-dependencies.txt` or run:
   ```apl
   ]tatin.InstallPackages APLPage
   ```
2. Rebuild or reload your workspace to include the APLPage namespace.

## Usage

1. Create or use an existing namespace as the template context. Assign any variables you want to inject:
   ```apl
     ctx←⎕NS ''           ⍝ Empty namespace
     ctx.Title←'My Site'
     ctx.UserName←'Alice'
   ```

2. Call the `GenPage` function with your context and the path to a `.aplp` file:
   ```apl
   html←ctx APLPage.GenPage 'APLPages/welcome.aplp'
   ```

3. Serve, display, or write the resulting `html` string as needed.

## Placeholder Syntax

In your `.aplp` template files, insert markers where dynamic content should appear:
```html
<h1><!--⋄ Title ⋄--></h1>
<p>Welcome, <!--⋄ UserName ⋄-->!</p>
```
The `GenPage` function will replace each `<!--⋄ Name ⋄-->` with the text value of `ctx.Name`.

## Directory Structure

```text
APLPage/
  cider.config         # Cider project configuration
  apl-package.json     # Tatin package descriptor
  APLSource/
    APLPage/
      APLPage.aplc     # Core GenPage implementation
```

## License
This project is released under the MIT License.

---
_Version 0.1.2_
