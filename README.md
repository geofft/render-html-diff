This is a tool to render visual diffs of the deployed version of a
website against the version in a local directory. The use case I built
it for was making sure that a new version of a static site renderer,
which generated an extremely noisy HTML diff, did not cause any actual
visible differences.

To use it, open [index.html](https://geofft.github.io/render-html-diff/)
in a browser, set the base URL to your deployed website (probably with a
trailing slash), and drag and drop your local directory (from
Finder/Explorer/etc.) onto the labeled target. If you want to see the
diff mode in action, try making a small textual change to your local
directory.

This tool runs entirely client-side, so your website needs to be
accessible by `fetch()`. If you're using the link above, that means you
need CORS enabled (which is generally fine for public websites).
Alternatively, you can upload a copy of the HTML file to your own
domain, so it's not cross-origin.

It uses [the approach outlined by Ron Valstar to render HTML to an
image](https://ronvalstar.nl/render-html-to-an-image) by converting
through an SVG `foreignElement` and an image tag, and then compares the
pixel-by-pixel renderings and generates an image with a black pixel
wherever the two renderings are different. You can click to see the old
and new renderings to pinpoint what changed.
