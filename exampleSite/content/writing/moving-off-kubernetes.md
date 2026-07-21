---
title: "Why we moved off Kubernetes"
date: 2026-03-14
---

Two years ago we ran a fifteen-node cluster to serve a workload that, in
hindsight, never needed one. This is the story of why we tore it down and what
replaced it.

## The workload

Most of our traffic is bursty but predictable: a handful of scheduled jobs and
a low-volume API. None of it needed autoscaling across machines — it needed
autoscaling across a single machine's cores, which is a *much* simpler problem.

The things we actually relied on were narrow:

- Restart a process when it dies
- Roll out a new binary without dropping requests
- Keep one Postgres instance healthy and backed up

Everything else in the cluster existed to support the cluster itself.

## What we run now

A handful of systemd units, one Postgres instance, and a deploy script that
rsyncs a binary and restarts the service. No orchestrator, no control plane, no
YAML.

```
systemctl enable --now waypoint.service
journalctl -u waypoint -f
```

The migration took three steps:

1. Move Postgres to a dedicated host and verify backups end to end.
2. Package each service as a single static binary with a systemd unit.
3. Point DNS at the new host and drain the cluster over a weekend.

It has been **eighteen months** and we have not missed it once.
