# Heroku CLI GitHub Action

GitHub Action that installs the Heroku CLI

This action installs the Heroku CLI on the runner.  Once installed it will be available in the PATH for subsequent steps in the job so you can just call `heroku`.

## Cache

When running on Linux, cache (actions/cache) is used to speed up the installation process.  The cache is invalidated monthly to ensure newer versions of the CLI are
installed.

## Authentication

This action only installs the CLI and does authenticate a user.  You will still need to ensure you are authenticated before using the CLI.  You can do this by setting the `HEROKU_API_KEY` environment variable.

## Example usage

```yaml
- name: Install Heroku CLI
  uses: ynab/heroku-cli-action@v1
- run: heroku whoami
  env:
    HEROKU_API_KEY: ${{ secrets.HEROKU_API_KEY }}
```
