# Browser Rendering Process

## Overview

When you visit a website, your browser goes through a series of steps to transform HTML, CSS, and JavaScript into the visual page you see. This process is called **rendering**.

## The Rendering Pipeline

### 1. Request & Response
- **User enters URL** or clicks a link
- **Browser sends HTTP request** to the server
- **Server responds** with HTML document

### 2. Parse HTML (DOM Construction)
- **Browser reads HTML** from top to bottom
- **Creates DOM (Document Object Model)** - a tree structure of all HTML elements
- **Discovers external resources** (CSS files, images, scripts)

### 3. Parse CSS (CSSOM Construction)
- **Browser downloads CSS files**
- **Parses CSS rules** and creates CSSOM (CSS Object Model)
- **Calculates styles** for each element

### 4. Render Tree Construction
- **Combines DOM and CSSOM** into a Render Tree
- **Excludes invisible elements** (like `display: none`)
- **Only includes elements** that will be displayed

### 5. Layout (Reflow)
- **Calculates exact position and size** of each element
- **Determines geometry** - where everything goes on the page
- **Considers viewport size** and responsive rules

### 6. Paint
- **Converts layout into pixels**
- **Draws text, colors, images, borders, shadows**
- **Creates layers** for complex elements

### 7. Composite
- **Combines all layers** in the correct order
- **Handles overlapping elements** and z-index
- **Displays final result** on screen

### 8. JavaScript Execution (Parallel Process)
- **JavaScript can modify DOM/CSS** at any time
- **Triggers re-rendering** if changes are made
- **May block rendering** if scripts are not async/defer

## Key Decision Points

- **Is CSS loaded?** → If no, wait before rendering
- **Is JavaScript blocking?** → If yes, pause HTML parsing
- **Did content change?** → If yes, recalculate layout and repaint
- **Are images loaded?** → If no, show placeholder, then reflow when loaded

## Performance Tips

- Minimize CSS and JavaScript file sizes
- Use async/defer for non-critical scripts
- Optimize images and use lazy loading
- Reduce layout thrashing (multiple reflows)
