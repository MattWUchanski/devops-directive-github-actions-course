# Test File for Workflow Triggers

This file is being modified to test the workflow trigger on pull requests.

The workflow is configured to run when:
- Files matching `03-core-features/filters/*.md` are modified
- A pull request is opened, synchronized, or reopened

This change should trigger the workflow defined in `.github/workflows/03-core-features--04-triggers-and-filters.yaml`.
