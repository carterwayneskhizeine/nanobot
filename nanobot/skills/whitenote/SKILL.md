---
name: whitenote
description: Manage WhiteNote posts and workspaces via local file sync system. Use for: (1) Creating new posts with tags, (2) Managing workspaces, (3) Reading post history, (4) Syncing markdown content to WhiteNote database
---

# WhiteNote Management

Manage WhiteNote collaboration platform via its local file synchronization mechanism.

## Environment Context

- **Root Sync Path**: `D:\Code\whitenote-data\link_md\`
- **Project Root**: `D:\Code\whitenote`

## Creating a New Post

To create a post, write a `.md` file to the specific workspace folder.

**File Path Rule**:
`D:\Code\whitenote-data\link_md\<Workspace-Name>\<Descriptive-Filename>.md`

**Content Format (Strict)**:
- **Line 1**: Tags starting with `#` (optional, recommended)
- **Line 3+**: Message content (supports multi-line)

**Example**:
```markdown
#idea #todo

This is the content of the post.
It will be synced to the database automatically.
```

## Managing Workspaces

- A **folder** in the root sync path equals a Workspace
- **Create workspace**: Use `mkdir` to create new folder in `D:\Code\whitenote-data\link_md\`
- **Ignore**: `.obsidian`, `.git`, `.DS_Store`, `.whitenote`

## Reading History

- Read markdown files within the target workspace directory to find content
- `.whitenote` folder contains metadata (`workspace.json`) - do not modify manually

## Execution Steps

1. **Identify Intent**: POST, READ, or CREATE workspace?
2. **Resolve Path**:
   - If workspace specified, verify it exists
   - If not specified, ask user or infer from context (e.g., code-related → `Codes`)
3. **Action**:
   - **Posting**: Generate descriptive filename, format content with tags on first line, write file
   - **Workspace**: Create directory
4. **Confirmation**: Inform user that file watcher will auto-sync changes

**Tip**: If user provides raw text dump, summarize into descriptive filename and extract keywords for tags.
