# raphaelweis.github.io

My personal website, made with [hugo](https://gohugo.io).
I wrote a hugo theme for this, code available at [raphaelweis/hugo-md3-theme](https://github.com/raphaelweis/hugo-md3-theme)

## Clone the theme

The theme is a submodule and you need to clone it before serving the site:
```
git submodule update --init --recursive
```

## Serve the website locally.

To serve the website locally and develop on it with live reload, ensure hugo is installed and run:

```bash
hugo serve -D --noHTTPCache
```

## Update the theme

If there has been an update to the site's theme, the submodule needs to be updated with:

```bash
git submodule update --remote --merge
```

## License

This website is licensed under the MIT license, along with it's theme. You are free to reuse any part of it as stated in the [LICENSE](/LICENSE).