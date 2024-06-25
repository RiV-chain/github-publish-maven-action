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
          distribution: 'adopt'
```

Add following lines in ```build.gradle``` build script:

```
publishing {
    repositories {
        mavenLocal()
    }
    publications {
        gpr(MavenPublication) {
            from(components.java)
        }
    }
}
```

Register ```secret.PAT``` with permission for you Maven repo and replace the path it in ```artifact_repo``` parameter.

# Notes:
  * Permissions: Ensure your repository permissions allow this action to perform the required tasks, including checking out repositories and pushing changes.
  * Secrets: Ensure the ```${{ secrets.PAT }}``` secret is set in your Maven GitHub repository secrets.
  * Java ```distribution``` parameter receives possible values: https://github.com/actions/setup-java?tab=readme-ov-file#supported-distributions.
