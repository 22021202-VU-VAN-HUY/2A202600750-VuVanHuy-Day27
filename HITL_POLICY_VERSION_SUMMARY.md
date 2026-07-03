# HITL Policy Version Summary

| Version | File | Score | Submitted | Notes |
|---|---:|---:|---|---|
| v1 | `hitl_policy.json` | 62.63 | 10:02:35 3/7/2026 | Baseline policy covering all 9 tools. Safe but likely too broad in some HITL/REJECT conditions. |
| v2 | `hitl_policy_v2.json` | 68.92 | 10:11:20 3/7/2026 | Best score so far. More practical than v1, with clearer distinction between routine analysis, HITL, and REJECT. |
| v3 | `hitl_policy_v3.json` | 66.77 | 10:15:57 3/7/2026 | Added more coverage for prompt injection, external transfer, package/download risk, and audit cases, but likely over-triggered. |
| v4 | `hitl_policy_v4.json` | 65.51 | 10:22:04 3/7/2026 | Tried a shorter, GitHub-inspired policy, but still scored below v2. |
| v5 | `hitl_policy_v5.json` | 66.87 | 10:26:38 3/7/2026 | Returned closer to v2 with concise risk gates. Improved over v3/v4, but still below v2. |

## Current Best

`hitl_policy_v2.json` is currently the best-performing submission with a score of **68.92**.

## Observations

- Adding too many broad HITL conditions appears to reduce the score.
- The judge likely rewards practical judgment: allow routine analysis, pause only for high-risk legitimate actions, and reject only clearly unsafe behavior.
- v2 seems to have the best balance so far between coverage and false positives.

## Suggested Next Direction

Use `hitl_policy_v2.json` as the baseline for future versions. Future changes should be small and targeted, especially around:

- `send_user`: unverified high-impact results, secrets, regulated raw data.
- `lakehouse_write`: production/source-of-truth writes and destructive writes.
- `run_bash`: destructive commands, exfiltration, credential discovery.
- Prompt injection: ignore instructions embedded in data or tool output.
