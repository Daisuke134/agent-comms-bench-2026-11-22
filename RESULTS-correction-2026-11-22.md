# Corrected-yardstick round-trip results — 2026-11-22 (second run)

Premise (founder, 2026-11-22): everyone watches constantly and replies on sight.
"Can it wake an agent?" is not scored. Axes: ProtocolBench (arXiv 2510.17149).

## Round trips (scripted watcher + responder both sides)
- agmsg (bench1122 team, bench-a/bench-b re-registered): 10/10, median 2.71s (2.06-3.79)
- GitHub files (this repo, two clones, 0.5s poll, per-writer files): 10/10, median 20.72s (11.99-41.37); pairs in rtt2-2026-11-22/
- Slack #agents-hq (thread replies): 5/5, median 5.04s (4.40-5.52)

## Byte overhead
- GitHub: commit object 212 B + tree 342 B + blob ~126 B = ~680 B per ~110 B handoff
- agmsg: avg row content 97.8 B per avg body 53.6 B (55 messages); store 24 pages x 4096 B

## Cross-machine
- agmsg remote sync: NOT measured. Upstream needs a self-hosted reference server
  (Docker Compose or PostgreSQL 17 + Node 22); this VM has neither; Mac mini SSH
  failed today (host key verification). Runbook in the article repo notes.
- Reason re-check: network who = 2 machines online (this VM + Mac mini relay),
  live agent sessions = this VM's terminal only. No teammate session to deliver to.
