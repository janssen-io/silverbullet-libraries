# Breadcrumbs

Creates a list of links to the parent pages of the provided page.

If no page is provided, the current page is used.

## Usage

Use `${crumbs.show()}` or `${crumbs.show("Path/To/Page")}` to shows the crumbs.

${crumbs.show()}

## Credits

This script was adapted from the scripts provided by Sebastian (yggi) on the
[SilverBullet community forum](https://community.silverbullet.md/t/breadcrumbs-for-hierarchical-pages/737/2?u=janssen-io).

## Lua

```space-lua
crumbs = crumbs or {}
function crumbs.build(path)
  local page = path or editor.getCurrentPage()
  local parts = string.split(page, '/')
  local crumbs = {}

  for i, part in ipairs(parts) do
    local current = ""
    for j=1, i do
      if current != "" then current = current .. "/" end
      current = current .. parts[j]
    end

    table.insert(crumbs, {name = current })
  end

  return crumbs
end

templates = templates or {}
templates.breadcrumbs = template.new([==[ › [[${name}]]]==])

function crumbs.show(path)
  return template.each(crumbs.build(path), templates.breadcrumbs)
end
```
