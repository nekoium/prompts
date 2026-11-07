Set up automatic Windows test builds for this Godot project on GitHub. Complete the setup and verify the first published download. Generate the workflow yourself from this project's requirements. Do not ask me to write or edit YAML.

Outcome:
- Each push to the repository's default branch builds a Windows x64 release export.
- A manual GitHub Actions trigger can also build the default branch.
- Each successful build publishes a ZIP as a GitHub prerelease in this repository.
- Collaborators only need to download the ZIP, extract it, and open the game executable. They do not need Git, Godot, or a launcher.
- Earlier builds remain available. A rerun for the same source commit can replace that commit's ZIP.
- Keep the repository's current visibility. Private builds require repository access. Do not make the repository public or place credentials in files.

Inspect before editing:
1. Read applicable project instructions. Inspect Git status, remotes, the actual remote default branch, existing workflows, project.godot, export presets, and build dependencies.
2. Check GitHub authentication, repository permissions, Actions settings, and branch rules. Use the authenticated GitHub CLI or an equivalent available integration. If authentication is missing, guide me through the normal browser sign-in. Never ask me to paste tokens into chat.
3. Determine the exact supported Godot version from project evidence. Check that the required official editor and export templates exist. Do not assume that a project feature version identifies an exact patch release. Ask only if project evidence cannot resolve a build-critical choice.
4. Check for .NET, Git LFS, submodules, plugins, generated dialogue data, and other required build steps. Use the appropriate editor and dependencies. Reuse existing working build steps where possible.
5. Preserve all unrelated local changes. Base remote work on the current remote default branch, not an outdated local checkout. Use a separate branch or isolated checkout when needed.

Implement the smallest complete workflow:
- Reuse or update an existing suitable workflow instead of adding a duplicate publisher.
- Trigger on pushes to the actual default branch and workflow_dispatch. Publish only from that branch. Do not publish pull request or fork code with write credentials.
- Install the project's Godot version and matching official export templates on an appropriate GitHub-hosted runner. Pin third-party actions to verified commit SHAs and use currently supported action runtimes.
- Use the project's Windows export preset. If none exists, create the smallest suitable Windows x64 preset without changing other platforms or game behavior.
- Compile required generated resources before import and export. Include runtime data required by the project.
- Keep tools, archives, temporary files, and export output outside Godot's imported/exported resources, or exclude them explicitly. Keep any local temporary files inside the project or isolated checkout and remove them when no longer needed.
- Run headless import and release export. Stop on command failures. Verify the expected executable exists and package all required output files in the ZIP.
- Give the ZIP a clear project name and commit identifier. Include the game version if the project defines one. Do not require a new version field just for this workflow.
- Use the full source commit SHA to identify the prerelease tag. Set its target to that exact commit. Keep older releases and replace the matching asset on reruns. Do not mark test builds as stable releases.
- Publish only after export and packaging succeed. Check release creation and upload failures. Avoid leaving a newly created release without its download if upload fails, for example by publishing a draft after upload succeeds.
- Limit token permissions to the jobs that need them. Do not persist checkout credentials unless a necessary step requires them. Add a reasonable build timeout.
- Do not cancel earlier builds automatically. Each push should be able to produce its own retained build.
- Include the download link in the workflow run summary.

Validate and activate:
1. Check the workflow syntax and applicable project checks. Inspect the diff for unrelated changes.
2. Push the setup on a dedicated branch and open a focused pull request. Validate import and export in GitHub Actions before merge, without publishing a test-branch release. Use a temporary branch trigger if needed, then remove it from the final workflow.
3. Fix failures caused by this setup and rerun the checks. If an existing game problem blocks export, explain the specific blocker. Do not silently change gameplay or report success.
4. This request authorizes the focused workflow commit, remote branch, pull request, merge, and first test prerelease. Merge once checks pass if repository rules permit. Never bypass required approvals or protections. If a rule blocks progress, finish all independent work and report the exact remaining action.
5. Verify a real default-branch run completes successfully. Confirm the prerelease contains the expected nonempty Windows ZIP. Do not stop after creating a workflow file or merely starting a run.
6. Preserve unrelated working files and remove only temporary files you created. Do not add extra planning documents or unrelated repository changes.

Finish with:
- The permanent Releases page link to share with collaborators.
- The first verified build link and workflow or pull request link.
- A short explanation: push to the default branch, wait for the build, download the ZIP, extract it, and open the executable.
- A reminder that private downloads require GitHub sign-in and repository access. Explain that /releases/latest excludes prereleases.
- Any actual blockers or validation limits. Distinguish successful build/export/upload from gameplay testing.

Make routine implementation decisions yourself. Ask only for missing information or permissions that block the work. Do not claim setup is complete until the first published download is verified.
