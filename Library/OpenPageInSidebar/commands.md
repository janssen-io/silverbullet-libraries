# Sidebar: Open Page

This command opens a page, picked from the page navigation picker, in the panel
on the right hand side.

Try it out: {[Sidebar: Open Page]}

```space-lua
command.define {
  name = "Sidebar: Open Page",
  key = "Ctrl-Alt-ArrowRight",
  run = function()
    local allPages = query[[
      from index.tag "page"
      order by _.lastModified desc
    ]]
    local page = editor.filterBox('➡️', allPages, "Select the page to open aside")
    if page != nil then
      editor.showPanel("rhs", 2, [[<iframe src = ]] .. page.name .. [[ style = "height: 98vh; width: 100%; border: 0;" />]])
    end
  end
}
```

## Sidebar: Close

To easily close this panel, the command {[Sidebar: Close]} is provided.

```space-lua
command.define {
  name = "Sidebar: Close",
  key = "Ctrl-Alt-ArrowLeft",
  run = function()
    editor.hidePanel("rhs")
  end
}
```