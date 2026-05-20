# Contributing to the registry

Two ways to contribute:

## Add or update a plug-in

1. Fork this repo.
2. Edit `plugins.json` — add a new entry or bump `latestVersion` on yours.
3. Update `lastUpdated` to today's date (ISO YYYY-MM-DD).
4. Open a PR.

For new submissions, the PR title should be `[ADD] yourorg.plugin.name`. For updates, `[UPDATE] yourorg.plugin.name vX.Y.Z`.

A maintainer will install your plug-in locally and verify it works as described before merging.

## Improve the registry itself

Open an issue first. Things that need discussion:

- Changes to `schema.json` (registry format)
- New required manifest fields
- Submission rules
- Tooling

PRs against `README.md` for typos and clarifications are welcome without prior discussion.

## What we reject

- Plug-ins that exist mainly to advertise something else
- Wrappers around proprietary services that don't disclose the integration in the description
- Submissions where the plug-in repo is private or hasn't cut a release
- Code that exfiltrates trace data without saying so

If your plug-in needs to send data outside the user's machine, say so explicitly in the description: "Sends trace summaries to Slack via your webhook." Hidden network calls fail review.
