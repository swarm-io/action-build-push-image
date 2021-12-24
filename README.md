<!-- start title -->

# GitHub Action:Build and Push image

<!-- end title -->
<!-- start description -->

Builds an image, pushes to artifact registry, and caches to gha as well as the `cache` tag. Specifically designed to work with artifact registry

<!-- end description -->
<!-- start contents -->
<!-- end contents -->
<!-- start usage -->

```yaml
- uses: swarm-io/action-build-push-image@undefined
  with:
    # gcloud service account credentials json
    credentials-json: ""

    # gcloud project id
    project-id: ""

    # artifact registry region
    # Default: us-west1
    region: ""

    # artifact registry repository
    # Default: images
    repository: ""

    # docker build secrets, comma separated string key=value
    # Default:
    secrets: ""

    # tag name, excluding tag version, such as `myapp`
    # Default: ${{ github.event.repository.name }}
    tag-name: ""

    # git tags to push, comma separated string such as `latest,v1.0.0`
    # Default: latest,${{ github.event.release.tag_name }}
    tag-versions: ""

    # git tag version to use for the registry cache
    # Default: cache
    cache-tag-version: ""
```

<!-- end usage -->
<!-- start inputs -->

| **Input**               | **Description**                                                  |                  **Default**                  | **Required** |
| :---------------------- | :--------------------------------------------------------------- | :-------------------------------------------: | :----------: |
| **`credentials-json`**  | gcloud service account credentials json                          |                                               |   **true**   |
| **`project-id`**        | gcloud project id                                                |                                               |   **true**   |
| **`region`**            | artifact registry region                                         |                  `us-west1`                   |  **false**   |
| **`repository`**        | artifact registry repository                                     |                   `images`                    |  **false**   |
| **`secrets`**           | docker build secrets, comma separated string key=value           |                                               |  **false**   |
| **`tag-name`**          | tag name, excluding tag version, such as `myapp`                 |     `${{ github.event.repository.name }}`     |  **false**   |
| **`tag-versions`**      | git tags to push, comma separated string such as `latest,v1.0.0` | `latest,${{ github.event.release.tag_name }}` |  **false**   |
| **`cache-tag-version`** | git tag version to use for the registry cache                    |                    `cache`                    |  **false**   |

<!-- end inputs -->
<!-- start outputs -->
<!-- end outputs -->
<!-- start examples -->

### Example usage with multiple secrets

```yaml
name: Build and push image to GAR
on:
  release:
    types: [created]
jobs:
  build-push-image:
    runs-on: ubuntu-latest
    steps:
      - uses: swarm-io/action-build-push-image@v1
        with:
          credentials-json: ${{ secrets.GAR_WRITE_SERVICE_ACCOUNT_KEY }}
          project-id: ${{ secrets.GCLOUD_PROJECT_ID_PROD }}
          secrets: |
            GIT_PAT=${{ secrets.GIT_RUNNER_TOKEN }}
            BUF_USER=${{ secrets.BUF_USER }}
            BUF_TOKEN=${{ secrets.BUF_TOKEN }}
```

<!-- end examples -->
<!-- start [.github/ghdocs/examples/] -->
<!-- end [.github/ghdocs/examples/] -->
