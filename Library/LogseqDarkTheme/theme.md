## Top Bar
The thingy right at the top with the page name and icons.

```space-style
#sb-top {
  height: 2em;
  background: transparent;
  border: none;
  margin: 0 0 5em 0;
  opacity: 0.5;
  transition: opacity 0.3s;

  &:hover {
    opacity: 1;
  }

  .main .inner {
    font-size: 1.2em;
    padding: 2ch 0;

    &::before {
      content: '📖';
    }

    button svg {
      height: 1.2em;
    }
  }
}

/* Mobile Toolbar */
@media only screen and (max-width: 600px) {
  #sb-top { opacity: 1 !important; }
  #sb-top .main .inner .sb-actions {
    position: fixed;
    bottom: 0;
    left: 0;
    padding-bottom: 30px;
    background: var(--top-background-color);
    width: 100vw;
    overflow-x: auto;
    box-shadow: 0px 4px 8px black;
    justify-content: space-around;
    
    button {
      padding: 1em 1em;
      margin: 5px 0 0 0;
      
      svg {
        height: 1.4rem;
        width: 1.4rem;
        margin: 0;
      }
    }
  }
}
```

## Top and Bottom Widgets
The things in the (invisible) box on top and bottom of the page.

```space-style
html {
  --editor-widget-background-color: rgba(0, 0, 0, 0) !important;
}

#sb-editor .cm-content .sb-markdown-top-widget:has(*) {
  padding-bottom: 15px;
  border-bottom: 1px solid gray;
  border-top: none;
}

#sb-editor .cm-content .sb-markdown-bottom-widget:has(*) {
  padding-top: 15px;
  border-top: 1px solid gray;
  border-bottom: none;
  margin-top: 80px;
}

#sb-editor .cm-content .sb-markdown-top-widget:has(*),
#sb-editor .cm-content .sb-markdown-bottom-widget:has(*) {
  border-left: none;
  border-right: none;
  border-radius: 0;
  opacity: 0.5;
  transition: opacity 0.3s;
  border-color: var(--panel-border-color);
  
  div.button-bar {
    z-index: 10;
    right: -1em;
  }

  &:hover {
    opacity: 1;

    h1 {
      margin-right: 0.2em;
    }
  }

  h1 {
    font-size: 1em;
    line-height: 1em;
    text-align: right;
    float: right;
    display: inline-block;
    font-style: italic;
    font-weight: normal;
    opacity: 0.8;
    padding: 0;
    transition: margin-right ease-in-out 0.3s;
  }
  .content > ul > li {
    margin-top: 1em;
  }
  ul {
    padding-inline-start: 1em;
    li {
      &::before {
        color: var(--ui-accent-text-color);
        content: "•";
        font-family: "Segoe UI";
        border-radius: 100px;
        font-size: 0.8em;
      }
    }
  }
  a.wiki-link {
    color: var(--root-color);
    background: transparent;
  }
}
```
## 1 Chapter One
* List!
* With
  * Nested
    * Bullets 🥳
    * And a very long line that is eventually going to wrap around just to see if that works without a monospace font.      
### 1.1 Section One 
With some text
### 1.2 Section Two
With some ==other text== and an image: [vgsn8zm3.bmp](https://notes.sh32.app/config/theme/vgsn8zm3.bmp)
#### 1.2.1 Subsection One
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea **commodo consequa**t. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur _sint occaecat_ cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.

abcdefghijklmnopqrstuvwxyz

# H1
## H2
### H3
#### H4

## Tags
#theme #space-style
```space-style
html {
  --editor-hashtag-color: var(--ui-accent-color) !important;
  --editor-hashtag-background-color: transparent !important;
  --editor-hashtag-border-color: transparent !important;
}
```
## Quote
> This is a beautiful quote!

```space-style
#sb-main .cm-editor .sb-blockquote-outside {
  text-indent: 1ch;
}
```
## Code
```space-style
#sb-main .cm-editor .cm-line:not(.sb-line-fenced-code ) > span.sb-code {
  background: color-mix(in srgb, var(--root-color) 10%, transparent) !important;
  padding: 2px;
  border-radius: 4px;
}
```

This is: `Sparta!`

## Highlights
```space-style
html[data-theme=dark] {
  #sb-editor span.sb-highlight, .highlight {
    background-color: color-mix(in hsl, var(--panel-background-color) 90%, white 10%) !important;
    color: hsla(0, 0%, 100%, 0.7) !important;
  }
}
```
This is a ==highlight==
## Table

Example table:
| Header 1 | Header 2 |
|----------|----------|
| Cell A | Cell B |
| Cell C | Cell D |
| Cell E | Cell F |

```space-style
html {
  --editor-table-head-background-color: transparent;
  --editor-table-head-color: color-mix(in srgb, var(--ui-accent-text-color) 70%, transparent);
  --editor-table-even-background-color: color-mix(in srgb, var(--ui-accent-color) 3%, transparent);
}

html[data-theme=dark] {
  --editor-table-head-background-color: transparent;
  --editor-table-head-color: color-mix(in srgb, var(--ui-accent-text-color) 70%, transparent);
  --editor-table-even-background-color: var(--panel-background-color);
}

#sb-main .cm-editor table {
  border-collapse: collapse;
  margin-top: 20px;
  
  thead {
    font-size: 1em;
    line-height: 0.8em;
  
    tr {
      font-weight: normal;
      opacity: 1;

      td {
        border-left: none;
        border-right: none;
        padding: 1ch 1.5ch;
      }
    }
  }
  td {
    border: 1px solid rgba(128, 128, 128, 0.4);
    padding: 1ch 1.5ch;

    &:first-child {
      border-left: none;
    }
    
    &:last-child {
      border-right: none;
    }
  }
}
```

## Transclusion
Section two: **Error:** Page not found: config/theme#1.2 Section Two
```space-style
#sb-editor .cm-content .sb-markdown-widget.sb-markdown-widget-inline {
  border: 1px solid var(--ui-accent-color);
  opacity: 0.6;
  padding: 20px;
  filter: grayscale(100%);
  transition: opacity 0.4s ease-in-out, filter 0.4s ease-in-out;

  &:hover {
    opacity: 1;
    filter: grayscale(0%);
  }
}

.highlight {
  background-color: var(--editor-highlight-background-color);
}
```

## Horizontal Ruler
```space-style
hr, .sb-line-hr {
  border-width: 2px;
  border-color: color-mix(in hsl, var(--panel-background-color) 80%, white);
    border-image-source: linear-gradient(
    to bottom,
    color-mix(in hsl, var(--panel-background-color) 75%, white) 0px,
    black 1px);
    border-image-slice: 1;
}
```

- - -
Above me is a ruler.
As well as below me.
- - -


## Other Styles

```space-style

html {
  --ui-font: Inter, "Segoe UI", sans-serif;
  /* --editor-font: "Fira Code Light", "Cascadia Code", monospace; */
  --editor-font: var(--ui-font);
  --editor-heading-color: black;
  --ui-accent-color: hsl(199, 81%, 31%);
  --ui-accent-text-color: hsl(204, 81%, 31%);
}

html[data-theme=dark] {
  --editor-heading-color: hsl(180, 7%, 60%);
  --root-color: hsl(180, 7%, 60%);
  --ui-accent-color: hsl(46, 100%, 37%);
  --ui-accent-text-color: hsl(51, 100%, 50%);

  --root-background-color: hsl(192, 100%, 11%);
  --panel-background-color: hsl(192, 94%, 14%);
  --panel-border-color: hsl(192, 87%, 20%);
}

.cm-line {
  line-height: 175% !important; 
}

.sb-line-fenced-code {
  padding: 0 10px !important;
}

.sb-line-blockquote {
  padding: 10px !important; 
  border-left-width: 3px !important;
  border-color: var(--ui-accent-color);
}

.cm-list-bullet {
  font-family: Hack, monospace;
  color: red;
}

.cm-list-bullet::after {
  color: color-mix(in hsl, var(--root-color) 70%, transparent 30%) !important;
}

#sb-main .sb-line-fenced-code {
  font-family: "Hack", monospace;
  line-height: 150% !important;
}

.sb-markdown-widget-inline {
  padding: 8px 4px;
  border-radius: 7px;
}

#sb-main {
  .sb-line-h2, .sb-line-h3, .sb-line-h4, h2, h3, h {
    padding-top: 1lh !important;
    padding-bottom: 3px !important;
  }
  
  .sb-line-h4, h4 {
    font-style: italic;
    font-weight: 100;
  }
}

.sb-unsaved .cm-line::after {
  background-color: var(--ui-accent-text-color);
  content: "  ";
  display: inline-block;
  height: 18px; width: 18px;

  mask-image: url('data:image/svg+xml,<svg width="18" height="18" fill="none" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path d="M5.75 3A2.75 2.75 0 0 0 3 5.75v12.5A2.75 2.75 0 0 0 5.75 21h4.249a2.112 2.112 0 0 1 .062-.593l.227-.907H7.5v-5.25a.75.75 0 0 1 .75-.75h6.603l1.435-1.435A2.258 2.258 0 0 0 15.75 12h-7.5A2.25 2.25 0 0 0 6 14.25v5.25h-.25c-.69 0-1.25-.56-1.25-1.25V5.75c0-.69.56-1.25 1.25-1.25H7v2.75A2.25 2.25 0 0 0 9.25 9.5h4.5A2.25 2.25 0 0 0 16 7.25V4.523c.358.06.692.23.952.49l2.035 2.035c.329.328.513.773.513 1.238v1.721c.07-.005.142-.007.213-.007h.002c.437 0 .875.087 1.285.261V8.287a3.25 3.25 0 0 0-.952-2.299l-2.035-2.035A3.25 3.25 0 0 0 15.714 3H5.75ZM8.5 7.25V4.5h6v2.75a.75.75 0 0 1-.75.75h-4.5a.75.75 0 0 1-.75-.75Z" fill="%23fff"/><path d="M19.715 11h-.002c-.585 0-1.17.223-1.615.67l-5.902 5.902a2.684 2.684 0 0 0-.707 1.247l-.458 1.831a1.087 1.087 0 0 0 1.319 1.318l1.83-.457a2.684 2.684 0 0 0 1.248-.707l5.902-5.902A2.285 2.285 0 0 0 19.715 11Z" fill="%23fff"/></svg>');

  margin: 0 5px;
}

/* Make Mermaid diagrams wider */
@media(min-width: 1200px) {
  .sb-fenced-code-iframe:has(iframe) {
    min-width: 80vw !important;
    iframe {
      margin-left: calc((100vw - var(--editor-width)) / -2 + 10vw) !important;
    }
  }
}

@media(min-width: 1600px) {
  .cm-line:has(table) {
    min-width: 50vw !important;
    margin-left: calc((100vw - var(--editor-width)) / -2 + 25vw) !important;
  }
}

.sb-table-widget:has(table) {
  table td {
    text-wrap-mode: wrap !important;
  }
}

```