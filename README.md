# mdbook-open-gh-issue

A preprocessor for [mdbook][] to add a "open github issue link" on every page.

[mdbook]: https://github.com/rust-lang/mdBook

It adds an "Open issue on GitHub for this file" link on the bottom of every page, linking directly to the source file.
It uses the configured `git-repository-url` as the base.

## Installation

If you want to use only this preprocessor, install the tool:

```
cargo install mdbook-open-gh-issue
```

Add it as a preprocessor to your `book.toml`:

```
[preprocessor.open-gh-issue]
command = "mdbook-open-gh-issue"
renderer = ["html"]
```

## Configuration

`mdbook-open-gh-issue` is configured using additional options under `[output.html]`:

```toml
[output.html]
# Required: Your repository URL used in the link.
git-repository-url = "https://github.com/$user/$project"

# The text to use in the footer.
# The link text is marked by `[]`
gh-issue-text = "Outdated info? [Open issue on GitHub.]"

# The issue template to use. Defaults to "issue-template.yaml"
# New issue will get "file" parameter set to the current page.
gh-issue-template = "issue-template.yaml"
```

To style the footer add a custom CSS file for your HTML output:

```toml
[output.html]
additional-css = ["gh-issue-open.css"]
```

And in `gh-issue-open.css` style the `<footer>` element or directly the CSS element id `gh-issue-open`:

```css
footer {
  font-size: 0.8em;
  text-align: center;
  border-top: 1px solid black;
  padding: 5px 0;
}
```

This code block shrinks the text size, center-aligns it under the rest of the content
and adds a small horizontal bar above the text to separate it from the page content.

Finally, build your book as normal:

```
mdbook path/to/book
```

## Acknowledgments

- [mdbook-open-on-gh](https://github.com/badboy/mdbook-open-on-gh)
