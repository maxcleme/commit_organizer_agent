# Commit Organizer Agent

An AI agent that organizes your latest WIP commit.

## Usage

```bash
docker sandbox run cagent -- --exec https://raw.githubusercontent.com/maxcleme/commit_organizer_agent/refs/heads/main/agent.yaml /organize
```

## Requirements

- [cagent](https://github.com/docker/cagent) CLI installed
- `ANTHROPIC_API_KEY` environment variable set
