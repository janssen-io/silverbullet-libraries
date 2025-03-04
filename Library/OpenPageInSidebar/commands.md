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

silverbullet.registerCommand(
    {name: "Sidebar: Close", key: "Ctrl-Alt-ArrowLeft"},
    async () => { await editor.hidePanel("rhs"); }
);
```