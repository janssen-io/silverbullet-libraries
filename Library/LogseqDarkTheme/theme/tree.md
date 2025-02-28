## Links
```space-style
html {
    --treeview-folder-background-color: transparent;
    --treeview-folder-border-color: transparent;
    --treeview-folder-color: var(--root-color);
    --treeview-page-background-color: transparent;
    --treeview-page-border-color: transparent;
    --treeview-page-color: var(--root-color);
}

#sb-main > .sb-panel, #sb-top > .panel {
  margin-top: -7em;
  flex: 0 !important;
  width: 40ch;

  & > iframe {
    min-width: 40ch;
  }
}

#sb-top > .panel {
  padding-left: 40ch; /* width does not work */
  z-index: 1;
}

#sb-main > .sb-panel {
  z-index: 500;
}

.treeview-root, .tree, .treeview-header {
  background-color: hsl(193, 82%, 17%);
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
  #sb-main > .sb-panel {
    width: 90vw;
    
    & > iframe {
      width: 90vw !important;
    }
  }
}

```