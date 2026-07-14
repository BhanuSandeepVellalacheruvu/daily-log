# Daily Log

This repository maintains a simple daily log through automated commits.

## How it works

A GitHub Actions workflow is configured in `.github/workflows/daily-log.yml`. It runs automatically every day at 8:00 AM IST. 

On every run, the workflow:
1. Checks out the repository.
2. Appends the current date and time (in UTC) to a file named `daily-log.md`. If the file doesn't exist, it creates it.
3. Commits the changes using the configured GitHub username and verified email so contributions are attributed correctly.
4. Pushes the changes directly to the default branch.

## How to change the schedule

To change the schedule, edit the `.github/workflows/daily-log.yml` file and modify the cron expression under `on.schedule`:

```yaml
on:
  schedule:
    # This runs at 2:30 AM UTC, which corresponds to 8:00 AM IST.
    - cron: '30 2 * * *'
```

You can use a site like [crontab.guru](https://crontab.guru/) to help generate the correct cron syntax for your desired time (remember that GitHub Actions uses UTC time).

## Manual Trigger

The workflow also includes a `workflow_dispatch` trigger, which means you can manually trigger a run at any time from the "Actions" tab in this repository.
