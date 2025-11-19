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