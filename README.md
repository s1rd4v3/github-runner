__Fork of https://github.com/samber/github-actions-runner__

# 👌 Github Actions self-hosted runner provisioning

> Simple Docker images for starting self-hosted Github Actions runner(s).

[Github official documentation for self-hosted runners.](https://help.github.com/en/actions/hosting-your-own-runners/adding-self-hosted-runners)

## 🚀 Quick start

Add your self-hosted runner from your repository settings:

- Go to repository > settings > actions
- Click on "Add runner"
- Copy the URL and token

```sh
# start a runner on your server

$ docker run -d \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v /tmp:/tmp \
    -e GH_REPOSITORY=xxxxxxxxxxxx \
    -e GH_RUNNER_TOKEN=xxxxxxxxxxxxx \
    -e GH_RUNNER_LABELS=label1,label2 \
    samber/github-actions-runner:latest
```

```yaml
# .github/workflows/main.yml

on:
  - push

jobs:
  example:
    runs-on: self-hosted
    steps:
      - name: Hello world
        run: echo "Hello world"
```
