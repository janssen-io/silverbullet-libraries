# Breadcrumbs

Creates a list of links to the parent pages of the provided page.

If no page is provided, the current page is used.

## Usage

Use `${crumbs.show()}` or `${crumbs.show("Path/To/Page")}` to shows the crumbs.

${crumbs.show()}

Use `${crumbs.children()}` and `${crumbs.siblings()}` to show a list of child and sibling pages:

### Children  (of [[Library/Breadcrumbs]])
${crumbs.children("Library/Breadcrumbs")}
### Siblings (of [[Library/EisenhowerMatrix/README]])
${crumbs.siblings("Library/EisenhowerMatrix/README")}
## Credits

This script was adapted from the scripts provided by Sebastian (yggi) on the
[SilverBullet community forum](https://community.silverbullet.md/t/breadcrumbs-for-hierarchical-pages/737/2?u=janssen-io).

## Lua

```space-lua
crumbs = crumbs or {}
function crumbs._build(path)
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

function crumbs._count(s, c)
  return #(string.gsub(s, "[^" .. c .. "]", "")) or 0
end

function crumbs.children(path)
  local page = path or editor.getCurrentPage()
  return query[[
    from index.tag "page"
    where ref != page
      and ref:startsWith(page)
      and crumbs._count(ref, "/") == crumbs._count(page, "/") + 1
    select "[[" .. name .. "]]"
  ]]
end

function crumbs.siblings(path)
  local page = path or editor.getCurrentPage()
  local lastIndex = page:reverse():find("/")
  local parent = string.sub(page, 1, #(page) - lastIndex) .. "/"
  if (1 != 1) then
    return { page, lastIndex, #(page) - lastIndex, parent}
  end
  return query[[
    from index.tag "page"
    where ref != page
      and ref:startsWith(parent)
      and crumbs._count(ref, "/") == crumbs._count(parent, "/")
    select "[[" .. name .. "]]"
  ]]
end

templates = templates or {}
templates.breadcrumbs = template.new([==[ › [[${name}]]]==])

function crumbs.show(path)
  return template.each(crumbs._build(path), templates.breadcrumbs)
end

```

