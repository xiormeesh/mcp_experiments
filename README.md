# Experiments!

This repo is a collection of MCP experiments (mostly for personal use), starting from scratch and slowly adopting best practices, the goal is to research building (and using existing) MCP servers for k8s daily operations: 
* running kubectl commands (also provided by google's [kubectl-ai](https://github.com/GoogleCloudPlatform/kubectl-ai)), 
* checking logs, metrics, traces
* detecting changes on the cluster
* troubleshooting the state of the cluster

## FastMCP + MCP inspector

First implementation following [MCP course from Anthropic](https://learn.deeplearning.ai/courses/mcp-build-rich-context-ai-apps-with-anthropic), this uses MCP server (stdio) implemented using FastMCP lightweight framework providing two tools: listing arxiv papers for a specific topic and retrieving details for a specific paper_id.

To launch [MCP inspector](https://modelcontextprotocol.io/docs/tools/inspector) (npm needs to be installed): 

`npx @modelcontextprotocol/inspector uv run research_server.py`

or

```
source .venv/bin/activate
fastmcp dev research_server.py
```

to run locally without the inspector (non-Claude mode)

`fastmcp run server.py`
or
`uv run python server.py`


## Bonus stuff

I'm also trying out `ruff` and `uv`, some usefull stuff

### uv

`uv init` to initialize it in a repo

`uv add $package_name1 $package_name2` to both install them and add to `pyproject.toml`

`uv run $filename` to execute a script

### ruff

`uv run ruff check`  to run linter

`uv run ruff check --fix` to autofix it

`uv run ruff format` to autoformat kinda like `goformat` (might be a good idea to add it to precommit)