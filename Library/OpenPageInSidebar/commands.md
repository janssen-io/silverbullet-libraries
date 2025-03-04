# Sidebar: Open Page

This command opens a page, picked from the page navigation picker, in the panel
on the right hand side.

Try it out: {[Sidebar: Open Page]}

```space-script
silverbullet.registerCommand(
        {name: "Sidebar: Open Page", key: "Ctrl-Alt-ArrowRight"},
        async () => {

    const allPages = (await syscall(
        'system.invokeFunction',
        'index.queryObjects',
        'page',
    ));

    const page = await editor.filterBox(
        '➡️',
        allPages.map((f) => {
            return {
                name: f.name,
                description: `🏷️ ${ f.itags.join(', ') } `,
            };
        }),
        "Select the page to open in the sidebar",
    );

    if (page) {  
        await editor.showPanel("rhs", 1, `<iframe src = "${page.name}" style = "height: 98vh; width: 100%; border: 0;" /> `);
    }
});
```

## Sidebar: Close

To easily close this panel, the command {[Sidebar: Close]} is provided.

```space-script
silverbullet.registerCommand(
    {name: "Sidebar: Close", key: "Ctrl-Alt-ArrowLeft"},
    async () => { await editor.hidePanel("rhs"); }
);
```