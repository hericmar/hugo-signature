---
title: "A smaller way to think about queues"
date: 2026-05-02
---

Most queue outages I have debugged were not throughput problems. They were
someone discovering, at the worst possible moment, that a job was not
idempotent.

## Two properties worth more than speed

If a job can run twice without harm and can be dropped without silent data
loss, almost every other operational question becomes easy. Retries stop being
frightening, and you can restart a worker mid-flight without paging anyone.

```
UPDATE jobs SET state = 'pending'
WHERE state = 'running' AND heartbeat < now() - interval '5 minutes';
```

That one statement replaces a surprising amount of machinery.
