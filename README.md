# desktop-action

Github Action to start Docker Desktop.

This github action is [experimental](https://docs.docker.com/release-lifecycle/#experimental).
It currently supports starting Docker Desktop on "linux" nodes (ubuntu-latest) in Github Actions.

**Important**: since mid September 2023, the action inconsistently fails on macOs runner. We have updated the action to use linux runners.

Note that the usage of Docker Desktop is subject to [Docker Desktop license agreement](https://docs.docker.com/subscription/desktop-license/).

After this step executes, Docker Desktop is ready and available, the docker CLI can be executed in subsequent "run" steps

By default, the action downloads the last version of Docker Desktop. But you can specify another one by providing the build URL from where the action can download the specific version:

```
jobs:
  test-docker-desktop:
    name: Test Docker Desktop installation and start
    runs-on: ubuntu-latest
    strategy:
      matrix:
        build-url: [ "latest", "https://desktop.docker.com/linux/main/amd64/122432/docker-desktop-4.24.0-amd64.deb" ]

    steps:
      - name: Start Desktop
        uses: ./start
        with:
          docker-desktop-build-url: ${{ matrix.build-url }}
```
