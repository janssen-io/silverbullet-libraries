# SilverBullet Libraries

This is my collection of themes (`space-style`), commands and functions (`space-script`),
and snippets and templates for [SilverBullet](https://silverbullet.md).

You can either manually download them and copy them into your space or use my plug (⚠️ Work In Progress):
[SilverBullet 🔌: GitHub Libraries](https://github.com/janssen-io/silverbullet-github-libraries-plug).

## Libraries

### Themes
[Logseq Dark Theme](./Library/LogseqDarkTheme/README.md)
```yaml
- "gh://janssen-io/silverbullet-libraries/Library/LogseqDarkTheme"
```

### Snippets
_None so far_

### Templates
[Eisenhower Matrix](./Library/EisenhowerMatrix/README.md)
```yaml
- "gh://janssen-io/silverbullet-libraries/Library/EisenhowerMatrix"
```

### Functions & Commands
[Open Page in Sidebar](./Library/OpenPageInSidebar/commands.md)
```yaml
- "gh://janssen-io/silverbullet-libraries/Library/OpenPageInSidebar"
```

## Contributing

Feel free to contribute your own libraries via a Pull Request or by opening an
issue.

1. New Libraries **MUST** be placed in the `Library` folder
2. `index.json` **MUST not** need to be updated manually. The workflow will
    automatically update this file when changes are pushed to main.
3. Libraries **MUST** contain some form of documentation. Either as a separate
   README.md in the root of the library folder or as part of one of the library
   pages.
4. Files that are not relevant to be downloaded into a space **MUST** be added
   to `ignore.txt`