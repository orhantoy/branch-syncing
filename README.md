# Branch syncing with GitHub workflows

Example of a `7.x` branch that follows a `main` branch.

```yml
name: Update 7.x ref to main

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/github-script@v2
      with:
        github-token: ${{secrets.GITHUB_TOKEN}}
        script: |
          github.git.updateRef({
            owner: context.repo.owner,
            repo: context.repo.repo,
            ref: 'heads/7.x',
            sha: context.sha,
            force: true
          })
```
