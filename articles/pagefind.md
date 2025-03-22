# Pagefind

I found [Pagefind](https://pagefind.app/) as a full text search for static sites.

> Pagefind is a fully static search library that aims to perform well on large sites, while using as little of your users’ bandwidth as possible, and without hosting any infrastructure.

So I added a small search button on the homepage and asked Claude to modify the style a bit. The best thing about this tool is that it is also a static index, meaning you don't have to keep the index server running in the back ground, once the index is generated, and the following snippet added to a page of your choice:

```
<link href="/pagefind/pagefind-ui.css" rel="stylesheet">
<script src="/pagefind/pagefind-ui.js"></script>
<div id="search"></div>
<script>
    window.addEventListener('DOMContentLoaded', (event) => {
        new PagefindUI({ element: "#search", showSubResults: true });
    });
</script>
```

You're good to go, it works perfectly with GitHub pages (what I'm using currently) or any other website framework such as Hugo. Alternatively, you can use it as a web server to host your static pages (add a --serve flag in the end, maybe it can update the index while new pages were generated).

Try it out in my [blog](https://yinan.me)!
