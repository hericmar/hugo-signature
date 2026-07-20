# Signature

A minimal single-page Hugo theme: a heading, a few sections, and a writing list.

## Use

Add the theme and enable it in your site config:

```yaml
theme: "signature"
```

## Configure

The home page is driven entirely by site params:

```yaml
title: "Your Name"          # the display name
params:
  subtitle: "Software Engineer"
  description: "One or two lines about you."
  projects:
    - title: Example App
      description: Manages your examples.
      url: "https://example.com"
  elsewhere:
    - title: "github.com/you"
      url: "https://github.com/you"
    - title: "you@example.com"
      url: "mailto:you@example.com"
```

## Writing

Drop Markdown files in `content/writing/`. They appear in the home-page list
and each renders as its own post page.

```markdown
---
title: "Why we moved off Kubernetes"
date: 2026-03-14
---

Body text, headings, lists, and code blocks all supported.
```

Preview locally with `hugo server` (add `-D` to include drafts).
