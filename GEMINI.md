# Aeon

The `aeon` MCP server connects to the user's own Aeon agent, an autonomous agent that runs skills on a schedule with GitHub Actions in their repo.

- If a tool call fails with an auth error, ask the user to run `/mcp auth aeon` and sign in with GitHub.
- Start with `setup_status` or `list_skills` to see what the agent has. Use `list_instances` and `switch_instance` if the user has more than one agent.
- `run_skill` starts a GitHub Actions run. Follow it with `list_runs` and `get_run`, then `read_output`.
- Tools that change things (`update_skill`, `update_strategy`, `update_soul`, `install_pack`, `update_instance_settings`) commit to the user's repo. Confirm with the user before calling them.
- Secrets are never readable over MCP. Point the user to their repo settings for those.
