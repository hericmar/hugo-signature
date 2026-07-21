---
title: "Every markdown feature, rendered"
date: 2026-07-21
---

This page exists to exercise the theme. It renders every markdown construct
Hugo supports out of the box, so any styling gap shows up in one place rather
than being discovered later in a real post.

## Headings

The page title above is the only `h1`. Body content starts at level two.

## Second-level heading

### Third-level heading

#### Fourth-level heading

##### Fifth-level heading

## Text formatting

Running copy can be **bold**, *italic*, ***bold and italic***, or
~~struck through~~. Inline `code` sits in the monospace face, and a
[link to another post](/writing/moving-off-kubernetes/) points inside the site
while [an external link](https://gohugo.io/) leaves it. Bare URLs autolink too:
https://gohugo.io/documentation/.

A line ending in two spaces  
forces a hard break without starting a new paragraph.

## Lists

Unordered, with nesting:

- Restart a process when it dies
- Roll out a new binary without dropping requests
  - Drain connections first
  - Wait for the health check to pass
- Keep one Postgres instance healthy and backed up

Ordered, with nesting:

1. Move Postgres to a dedicated host
2. Package each service as a static binary
   1. Build reproducibly
   2. Ship the systemd unit alongside it
3. Point DNS at the new host

Task lists:

- [x] Verify backups end to end
- [x] Package the services
- [ ] Decommission the old cluster

## Blockquote

> The things we actually relied on were narrow. Everything else in the cluster
> existed to support the cluster itself.
>
> — from an internal postmortem

## Code

A fenced block with a language hint:

```go
func main() {
	http.HandleFunc("/healthz", func(w http.ResponseWriter, r *http.Request) {
		w.WriteHeader(http.StatusOK)
	})
	log.Fatal(http.ListenAndServe(":8080", nil))
}
```

A fence with no language, for shell transcripts and plain output:

```
systemctl enable --now waypoint.service
journalctl -u waypoint -f
```

## Table

| Service    | Runtime | Memory | Restarts |
| ---------- | ------- | -----: | -------: |
| waypoint   | Go      | 64 MB  |        0 |
| ledger     | Go      | 48 MB  |        2 |
| shelf-sync | Rust    | 32 MB  |        0 |

## Image

![A placeholder illustration](/img/example.svg)

## Horizontal rule

The rule below separates sections without a heading.

---

## Footnotes

Claims that need a source can carry one[^1], and footnotes may be referenced
more than once[^2].

[^1]: The footnote list is rendered at the bottom of the page, with a return link.
[^2]: Numbering follows reference order, not definition order.
