# NNO wiki — Claude notes

This is a [Quartz](https://quartz.jzhao.xyz/) wiki. Content lives under `content/` as Markdown with Obsidian-style `[[wikilinks]]`. The site is built by Quartz from the repo root.

## Math formatting

Math is rendered by `remark-math` + KaTeX (configured in `quartz.config.ts` via `Plugin.Latex({ renderEngine: "katex" })`).

**Block math (`$$...$$`)** must be written with the delimiters on their own lines and a blank line above and below. Otherwise it gets parsed as inline and rendered inline.

Do this:

```markdown
Some intro text.

$$
f(x) = x^2 + 1
$$

More text.
```

Not this:

```markdown
Some intro text.
$$f(x) = x^2 + 1$$
More text.
```

Inline math `$...$` is fine on any line, no spacing requirements.

## Links

Use Obsidian-style wikilinks with the full path from `content/`:

- `[[concepts/semialgebraic]]` — link by page
- `[[concepts/semialgebraic|semialgebraic sets]]` — with custom label

## Page conventions

- Every page starts with YAML frontmatter containing at least `title:`.
- Concept pages live in `content/concepts/`, lecture notes in `content/lectures/`.
- New concepts should also be linked from `content/concepts/index.md`.
- New lectures should also be linked from `content/lectures/index.md`.
