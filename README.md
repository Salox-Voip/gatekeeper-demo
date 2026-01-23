# gatekeeper-demo
Gatekeeper Demo.
=======
Gatekeeper demo for GitHub Actions environment gates and required reviewers.

## What this shows
- Environment protection rules (required reviewers) on `stage` and `prod`.
- Environment-scoped variables used inside jobs.
- PR open/close summaries and a manual run gated by environments.

## Setup (one-time)
1. In repo Settings -> Environments, create `stage` and `prod`.
2. Add required reviewers for both environments.
3. Add environment variables:
   - `STAGE_ENV_SAMPLE` in `stage`
   - `PROD_ENV_SAMPLE` in `prod`

## Workflows
- `.github/workflows/pr-open-summary.yml`: Runs on PR open to `stage`/`prod`, reads the environment variable, and writes a run summary.
- `.github/workflows/pr-close-summary.yml`: Runs when those PRs are closed and writes a summary with merge status.
- `.github/workflows/manual-env-gate.yml`: Manual workflow with an environment selector; required reviewers will gate the job.

## Demo script (quick)
1. Open a PR targeting `stage` or `prod` to show environment gating + run summary.
2. Close or merge the PR to show the close summary.
3. Manually run "Manual Environment Gate" and select an environment to trigger approvals.
