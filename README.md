# Track Dependencies

A GitHub Actions workflow that monitors specific files in upstream repositories for changes across releases.

## Usage

1. Copy `.github/workflows/check-upstream.yml` to your repository
2. Configure the environment variables in the workflow:
   - `MONITORED_REPO`: The upstream repository to track (e.g., `owner/repo`)
   - `CURRENT_VERSION`: Your current version (e.g., `v2.15.4`)
   - `FILES_TO_MONITOR`: List of files to check for changes
   - `INCLUDE_PRERELEASE`: Whether to include pre-releases (`true`/`false`)
   - `INCLUDE_DRAFT`: Whether to include draft releases (`true`/`false`)
   - `CREATE_PR`: Create a PR on changes instead of failing [not implemented yet] (`true`/`false`)

## How It Works

- Runs daily at 2 AM UTC (configurable via cron schedule)
- Checks for new releases in the monitored repository
- Compares specified files between your current version and the latest release
- Fails the workflow if changes are detected in tracked files

## Use Case

Useful when you've vendored or copied specific files from an upstream dependency and need to be notified when those files change in newer releases.