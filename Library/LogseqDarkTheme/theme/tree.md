## Treeview
```space-style
html[data-theme=dark] {
    --treeview-folder-background-color: transparent;
    --treeview-folder-border-color: transparent;
    --treeview-folder-color: var(--root-color);
    --treeview-page-background-color: transparent;
    --treeview-page-border-color: transparent;
    --treeview-page-color: var(--root-color);

  .treeview-root, .tree, .treeview-header {
    background-color: var(--panel-background-color);
  }
}

/* Use .first-child:is(.sb-panel) to only target the left panel */
#sb-main > div:first-child:is(.sb-panel),
#sb-top > :first-child:is(.panel) {
  margin-top: -7em;
  min-width: 40ch;
  max-width: 60ch;

  & > iframe {
    min-width: 40ch;
  }
}

#sb-main > :first-child:is(.sb-panel) {
  z-index: 500;
}

.treeview-actions {
  border: 0;
}

html:has(.treeview-root) {
  scrollbar-width: none;
  opacity: 0.4;
  transition: opacity 0.3s;
  font-family: Inter, "Segoe UI", sans-serif !important;

  &:hover {
    opacity: 1;
  }

  body {
    background-color: var(--panel-background-color);
  }
}

.tree {
  gap: 10px;
  padding-bottom: 10px;
  
  .tree__node[data-node-type="folder"][open=true]{
    margin-bottom: 12px;
  }
  
  & > .tree__node > .tree__label > span {
      font-weight: bold;
  }

  & .tree__label > span {
    font-family: Inter, "Segoe UI", sans-serif !important;

    &[data-current-page="true"] {
      background-color: var(--panel-border-color) !important;
    }
  }
}

@media only screen and (max-width: 600px) {
  #sb-main > div:first-child:is(.sb-panel) {
    width: 90vw;
    
    & > iframe {
      width: 90vw !important;
    }
  }
}

```