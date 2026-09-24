---
id: help.workspace.files_and_artifacts
title: Files And Artifacts
audience: user
status: verified
source_cards:
  - moclaw.concepts.workspace_file_and_artifact
  - moclaw.concepts.memory_and_personalization
  - moclaw.how_to.use_artifacts
  - moclaw.reference.file_preview_limits
  - moclaw.reference.file_preview_renderers
last_reviewed_at: 2026-07-23
---

# Files And Artifacts

MoClaw uses two related file concepts:

- **Workspace files** are files in the current AI Cloud Computer workspace.
- **Artifacts** are files MoClaw has surfaced as user-facing outputs, usually so
  you can open, reuse, download, or share them.

The same task can involve both. For example, MoClaw may work on several
workspace files, then publish the final report as an artifact.

Workspace memory files, such as `MEMORY.md` or a `memory/` folder, are workspace
files in the AI Cloud Computer. They are not automatically published artifacts.

## Where To Find Workspace Files

The current web app does not expose an **All files** browser for the full
workspace tree. Files already surfaced in Chat can open in that Chat's Dock.
For another workspace file, ask MoClaw to locate and present it.

## Where To Find Artifacts

1. Open **Artifacts** from the left navigation.
2. Find the source Session group.
3. Open a file in that Session's Dock, refresh the list, or download a
   supported file.

## Preview And Download

Not every file can be previewed. Some file types are binary, some previews need
time to prepare, and some files are too large for a specific preview renderer.
Download limits are separate from preview limits.

If preview fails but **Download original** is available, use the download
action. If download is disabled, check whether the file is larger than the
current workspace transfer limit.

For generated code or diagrams, `.html`, `.htm`, `.jsx`, `.tsx`, `.mmd`, and
`.mermaid` have special preview behavior. A live preview or diagram error is a
rendering issue, not automatic proof that the file was deleted.

## When Something Looks Missing

- Refresh **Artifacts** or reopen the file from Chat.
- Check whether the file was published as an artifact or only exists in the
  workspace.
- If you are looking for memory files, ask MoClaw to locate `MEMORY.md` or the
  `memory/` folder.
- Ask MoClaw to reference the file again if you know its name.
- If the same file still cannot open, capture the file name, visible path, file
  size, and approximate time.

## Related Articles

- `workspace/preview-generated-files.md`
- `workspace/upload-or-reference-files.md`
- `troubleshooting/common-errors.md`
