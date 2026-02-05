# Browser Rendering Process

## Overview

When you visit a website, your browser transforms HTML, CSS, and JavaScript into the visual page you see.

## The Rendering Pipeline

### 1. Fetch HTML
Browser requests and receives HTML from the server.

### 2. Build DOM
Parse HTML and create a tree structure of elements.

### 3. Build CSSOM
Download and parse CSS to understand styling rules.

### 4. Create Render Tree
Combine DOM and CSSOM, excluding hidden elements.

### 5. Layout
Calculate position and size of each element.

### 6. Paint
Draw pixels (text, colors, images) on screen.

## Activity Diagram

```mermaid
graph TD
    Start([User Enters URL]) --> Request[Send HTTP Request]
    Request --> Receive[Receive HTML]
    Receive --> ParseHTML[Parse HTML]
    
    ParseHTML --> HasCSS{CSS Found?}
    HasCSS -->|Yes| LoadCSS[Load CSS]
    HasCSS -->|No| BuildDOM[Build DOM]
    LoadCSS --> BuildDOM
    
    BuildDOM --> BuildCSS[Build CSSOM]
    BuildCSS --> RenderTree[Create Render Tree]
    
    RenderTree --> Layout[Calculate Layout]
    Layout --> Paint[Paint Pixels]
    Paint --> Display[Display on Screen]
    
    Display --> HasJS{JavaScript?}
    HasJS -->|Yes| RunJS[Execute JavaScript]
    HasJS -->|No| End([End])
    
    RunJS --> Changed{DOM Changed?}
    Changed -->|Yes| Layout
    Changed -->|No| End
```
