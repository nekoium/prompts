# Godot auto build

Set up automatic Windows builds for a Godot project on GitHub.

After setup, each push to the default branch creates a Windows ZIP under GitHub Releases. Earlier builds remain available.

Collaborators download the ZIP, extract it, and open the game. They do not need Git, Godot, or a launcher.

## Use

1. Open your Godot project in a coding agent that can edit files and run commands.
2. Copy the full text of [prompt.md](prompt.md).
3. Paste the text into your agent.
4. Complete GitHub sign-in if the agent requests it.

The agent inspects your project, creates the workflow, and checks a real build. You do not need to supply a YAML file.

The agent needs GitHub access to create branches, pull requests, workflows, and releases. Repository rules can require your approval before merge.

## Downloads

Share your repository's Releases page:

```text
https://github.com/OWNER/REPOSITORY/releases
```

The workflow publishes test builds as prereleases. GitHub does not include prereleases at `/releases/latest`.

For private repositories, collaborators must sign in and have repository access. Public repository builds are public.

## Scope

The prompt targets Windows x64 builds. It adapts to the project's Godot version, export settings, and build steps.

GitHub Actions usage and storage can incur charges under your account's plan. Downloaded games can trigger Windows security warnings.

The agent verifies build and upload results. A successful export does not prove that every part of the game works.
