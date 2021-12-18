<!-- start title -->
<!-- end title -->
<!-- start description -->
<!-- end description -->
<!-- start contents -->
<!-- end contents -->
<!-- start usage -->
<!-- end usage -->
<!-- start inputs -->
<!-- end inputs -->
<!-- start outputs -->
<!-- end outputs -->
<!-- start examples -->
### Example usage
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
          secrets: 'gitPat=${{ secrets.GIT_RUNNER_TOKEN }}'
```
<!-- end examples -->
<!-- start [.github/ghdocs/examples/] -->
<!-- end [.github/ghdocs/examples/] -->
