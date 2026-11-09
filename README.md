# Famous Repos Research: data

**How much of GitHub's most-starred AI tooling is written by coding agents?**

This repository holds the data behind the study published at **[www.soufraz.com/famous-repos-research](https://www.soufraz.com/famous-repos-research/)**: a full-history audit of 52 of GitHub's most-starred AI-tooling repositories (324,088 authored commits), compared with 12 famous pre-Copilot projects at the same age.

→ **[Read the study](https://www.soufraz.com/famous-repos-research/)** for the findings, charts, limits and FAQ, or the [written report](report.md) in this repository.

## Key results

- 38 of 52 repositories sign at least 5% of their commits with an AI signature (all-time or in their last 180 days of activity); 9 more commit coding-agent instructions while signing less; 5 show neither signal (unknown, not "no AI").
- In the median repository, 16.9% of the commits in its last 180 days of activity are AI-signed, a lower bound; 21 of 52 are at 25% or more.
- AI share does not predict stars (Spearman ρ = -0.05, p = 0.72).
- At six months old, the cohort labels 34.1% of its commits as fixes against 17.3% for the baseline, and keeps 67.1% of the lines it ever wrote against 41.7%. The fix share, churn and survival gaps are concentrated in the 31 projects started in 2025 or later: among them, repositories that sign at least 5% of their commits and those that sign less show no detectable difference, and the 10 cohort projects started earlier do not differ detectably from the baseline. Heavy AI use is concentrated in the newest projects (AI share vs start date: ρ = 0.72), so this sample cannot separate AI use from recency.
- 15 repositories publish outcome benchmarks with a runnable harness and committed results; several publish results that went against them.

The study is descriptive: the repositories are survivors chosen by today's stars from AI-tooling topics, AI shares are lower bounds, a signature says nothing about how carefully code was reviewed, and the published results are the authors' own, located but not re-run. See the site for the full list of limits.

## What is here

| Path | Contents |
| --- | --- |
| [`findings.json`](findings.json) | Every number shown on the site and in the report, with the statistics behind it |
| [`repos/`](repos) | One file per audited repository (52): stars, AI attribution, agent configuration, fix share, churn, survival, hotspots and a sample of recent commits |
| [`evidence/`](evidence) | What each repository publishes about its own performance: every claim with the file and line it appears on at the audited commit, its evidence type, and a note |
| [`snapshots/cohort/`](snapshots/cohort), [`snapshots/baseline/`](snapshots/baseline) | Each repository measured at day 180 and day 365 after its first commit; the baseline is 12 famous pre-Copilot projects |
| [`cohort/topics-2026-11-08.json`](cohort/topics-2026-11-08.json) | The top 10 repositories of each of the 7 GitHub topics on 2026-11-08 |
| [`cohort/shared_history.json`](cohort/shared_history.json) | Repository pairs that share git history (their shared commits count in both) |
| [`scorecard.csv`](scorecard.csv) | One row per repository |
| [`related_work.json`](related_work.json) | Papers and reports cited, each checked against its source |
| [`report.md`](report.md) | The written report |

## Definitions

- **Cohort.** The top 10 by stars in each of 7 GitHub topics (`agent-harness`, `ai-agents`, `coding-agents`, `context-engineering`, `llm`, `prompt-engineering`, `spec-driven-development`) on 2026-11-08, minus reading material and collections (books, courses, guides, prompt collections, awesome-lists), plus the 4 repositories the study started from (OmniRoute, context-mode, rtk, superpowers). No other repository was left out.
- **Commits.** Full history of the default branch; merge commits and maintenance bots (dependabot, release bots and similar) are excluded from every percentage.
- **AI-signed.** A commit carries an AI co-author trailer, an AI agent as author or committer, or a tool's "Generated with" footer, matched on the identities the tools write. A repository is AI-signed when at least 5% of its commits are, all-time or in its last 180 days of activity (counted back from its latest commit).
- **Agent configuration.** Coding-agent instruction files committed at the repository root (`CLAUDE.md`, `AGENTS.md`, `.cursor/`, `.github/copilot-instructions.md`, ...) or a coding agent run in CI. In AI-tooling repositories these can be product templates.
- **Fix %.** Share of commits whose subject contains fix, bug, hotfix or regression. Keyword-based, not a defect rate.
- **Churn ratio.** Lines added plus deleted over all history, divided by lines at HEAD. **Survival %**: lines at HEAD divided by lines ever added. Both cover source code and Markdown, excluding vendored, generated, translated, lock and changelog files.
- **Age-matched snapshots.** Each repository checked out at its last mainline commit 180 and 365 days after its first commit. Cohort snapshots taken before GitHub Copilot's general availability (2022-06-21) are left out of the comparison.
- **Evidence types.** `harness+results`: a runnable script and committed results; `results_only`: results without a script; `harness_only`: a script without committed results; `external`: a third-party evaluation; `claim_only`: a number without method or data. `result_focus` separates `outcome` results (does the tool do its job) from `engineering` results (speed of the software).

## Prepared for publication

- Contributor email addresses are removed; AI tool identities such as `noreply@anthropic.com` stay, because they are what is measured.
- Commit samples keep subjects, authors and AI signals, not message bodies.
- Unvalidated composite scores from an early version of the project are not included.
- A small amount of third-party text (two repository descriptions, some sampled commits and one quoted benchmark row) is omitted at the author's discretion; no number used in the study depends on it.
- The analysis code is not published yet.

## License and citation

The data and text in this repository are licensed under [CC BY 4.0](LICENSE). Quoted claims in `evidence/` belong to the repositories they come from and are cited with their file and line.

```bibtex
@misc{frazao2026agents,
  title  = {How much of GitHub's most-starred AI tooling is written by coding agents?},
  author = {Frazao, Rafael},
  year   = {2026},
  note   = {Data as of 2026-11-08; data: https://github.com/Soufraz/famous-repos-research-data},
  url    = {https://www.soufraz.com/famous-repos-research/}
}
```
