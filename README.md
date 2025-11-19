# probable-fiesta

This repository includes automated workflow failure tracking.

## Features

### Workflow Failure Tracking

The repository automatically monitors all GitHub Actions workflows. When a workflow fails:
- An issue is automatically created with details about the failure
- The issue includes the workflow name, branch, commit, and link to the failed run
- If the same workflow fails again, the existing issue is updated with a comment
- Issues are labeled with `workflow-failure` and `automated` for easy filtering

This helps ensure that workflow failures are properly tracked and don't go unnoticed.

#### How It Works

The workflow is triggered by the `workflow_run` event, which fires whenever any workflow in the repository completes. If the conclusion is `failure`, the tracking workflow:

1. Checks if an issue already exists for this workflow and branch combination
2. If no issue exists, creates a new one with:
   - Workflow name and branch
   - Commit SHA and triggering user
   - Link to the failed workflow run
   - Associated pull request numbers (if applicable)
3. If an issue already exists, adds a comment with details of the new failure

#### Configuration

The workflow is located at `.github/workflows/track-failed-workflows.yml` and requires the following permissions:
- `issues: write` - to create and update issues
- `actions: read` - to read workflow run information
- `contents: read` - to access repository content

No additional configuration is needed - the workflow automatically monitors all workflows in the repository.