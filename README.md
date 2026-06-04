# Commit Organizer Agent

An AI agent that splits your latest messy WIP commit into clean, logical, atomic commits that tell a clear story.

## How it works

- Separates tidying/structure changes from behavior changes, committing docs and tests before implementation
- Studies your `git log` to match your historical commit message style
- Aims for at most ~5 commits with ~5 changes each, ordered as a sequential story
- Validates the result by diffing against the original WIP commit SHA to guarantee no code was added, removed, or altered

## Usage

```bash
sbx run docker-agent -- \
    run --exec --yolo https://raw.githubusercontent.com/maxcleme/commit_organizer_agent/refs/heads/main/agent.yaml \
    /split_last_wip_commit
```

## Requirements

- [docker-agent](https://github.com/docker/docker-agent) CLI installed
- [sbx](https://github.com/docker/sbx-releases) CLI installed
- `ANTHROPIC_API_KEY` environment variable set

> [!IMPORTANT]
> Make sure you do **not** have a `GITHUB_TOKEN` environment variable defined, for two reasons:
>
> 1. GitHub credentials are not needed to operate on local git operations.
> 2. If one is incorrectly set (e.g. using the 1Password CLI with values starting like `op://`), it will trip the fetch request: your invalid GitHub credentials get injected at the `sbx` proxy level and cause the request to fail with a `404`.
