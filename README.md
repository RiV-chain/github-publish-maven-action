# github-publish-maven-action
Build Java project with Gradle, extract metadata, and publish artifacts to a repository.

# Usage in a Workflow

You can use this action in your workflows. Here's an example of how to use it:

```
name: Build and Publish

on:
  workflow_dispatch:

jobs:
  build-and-publish:
    runs-on: ubuntu-latest
    steps:
      - name: Use Maven publish action
        uses: RiV-chain/github-publish-maven-action@main
        with:
          gh_pat: ${{ secrets.PAT }}
          artifact_repo: 'RiV-chain/artifact'
          gradle_file_path: './gradlew'
          java_version: '8'
```

# Notes:
  * Permissions: Ensure your repository permissions allow this action to perform the required tasks, including checking out repositories and pushing changes.
  * Secrets: Ensure the ```${{ secrets.PAT }}``` secret is set in your Maven GitHub repository secrets.
