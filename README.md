# github-self-hosted-runner

```Bash
docker build . --file ./Dockerfile --tag ghcr.io/stkr22/github-self-hosted-runner:main
```

Get a valid token:
https://github.com/settings/tokens/new?scopes=repo

```Bash
docker create --name {{ github_runner_url }} \
    -e RUNNER_NAME={{ github_runner_url }} \
    -e GITHUB_ACCESS_TOKEN={{ github_pat_scope_repo }} \
    -e RUNNER_REPOSITORY_URL={{ github_repo_url }} \
    -v /var/run/docker.sock:/var/run/docker.sock \
    ghcr.io/stkr22/github-self-hosted-runner:main
docker start {{ github_runner_url }}
```


Sources
- https://github.com/wbond/pi-github-runner/blob/master/Dockerfile-base
- https://github.com/tcardonne/docker-github-runner
- https://github.com/actions/runner/releases
- https://docs.github.com/en/rest/reference/actions#self-hosted-runners
- https://stackoverflow.com/questions/59563916/how-i-can-get-a-github-actions-runner-token/65297314#65297314
- https://docs.github.com/en/rest/reference/actions#create-a-registration-token-for-a-repository
- https://docs.github.com/en/actions/hosting-your-own-runners/adding-self-hosted-runners
