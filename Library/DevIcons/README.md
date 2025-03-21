# DevIcons
Little helper function to display development icons as images inline in your text.

## Credits
Originally posted by [Maarrk](https://github.com/Maarrk): https://github.com/silverbulletmd/silverbullet/issues/125

## Function
```space-lua
function devicon(name)
  local cdn =
    "https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/"
  local icon = name .. '/' .. name .. '-original.svg'
  return widget.new {
    html = '<img src="' .. cdn .. icon .. '"/>',
    display = "inline",
    cssClasses = { "inline-icon" }
  }
end
```

```space-style
.inline-icon > img {
  height: 1.2em;
  width: 1.2em;
}
```

## Example
Text containing an icon for TypeScript ${devicon 'typescript'} thanks to Lua ${devicon 'lua'} 

## List of supported icons
Icons are taken from the CDN of [DevIcons](https://devicon.dev) ${devicon "devicon"}. Their website provides a search and preview function. A plain list overview available on [GitHub](https://github.com/devicons/devicon/tree/master/icons) ${devicon "github"}.

