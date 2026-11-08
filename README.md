# bookmarks-example

A minimal example of keeping bookmarks in [`bookmarks.md`](bookmarks.md) and publishing them to
GitHub Pages with [bookmarks](https://github.com/damian-krawczyk/bookmarks). The repository holds
only the bookmarks file and a workflow. The tool is installed when needed.

## Edit locally

Install the tool once:

```sh
npm install -g https://codeload.github.com/damian-krawczyk/bookmarks/tar.gz/main
```

Then, in this folder:

```sh
bookmarks serve bookmarks.md --open           # edit in the browser at http://127.0.0.1:4180/
bookmarks validate bookmarks.md               # check the file
bookmarks build bookmarks.md -o dist/index.html   # the read-only page, works offline
```

Run the install command again to update the tool. If zsh says `command not found: bookmarks`
right after installing, run `rehash` or open a new terminal.

## Publish to GitHub Pages

[`.github/workflows/pages.yml`](.github/workflows/pages.yml) installs the tool, validates
`bookmarks.md`, builds `dist/index.html` and deploys it on every push to `main` that changes
`bookmarks.md`.

One-time setup: in the repository, go to **Settings → Pages → Source** and choose
**GitHub Actions**. To redeploy without a change (for example after the tool was updated), run
the workflow from the **Actions** tab (*Run workflow*).

The published page is read-only. To change bookmarks, run `bookmarks serve` locally, then commit
and push `bookmarks.md`.
