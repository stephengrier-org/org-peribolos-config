# Peribolos configuration for managing the stephengrier-org GitHub organisation

## Creating an initial beribolos configuration

Peribolos can generate an initial configuration for an existing GitHub
organisation like so:

```bash
docker run --rm -v $PWD:/working gcr.io/k8s-prow/peribolos --dump stephengrier-org --dump-full --github-token-path /working/.access-token | tee ./config.yaml
```

## Deploying changes

Configuration changes can be tested like so:

```bash
docker run --rm -v $PWD:/working gcr.io/k8s-prow/peribolos --config-path /working/config.yaml --github-token-path /working/.access-token --fix-org
```

When you're happy with the output you can apply the changes for real with the
`--confirm` flag:

```bash
docker run --rm -v $PWD:/working gcr.io/k8s-prow/peribolos --config-path /working/config.yaml --github-token-path /working/.access-token --fix-org --confirm
```

### Adding/removing members to/from the org

Members can be added or deleted from the `members` list. The changes can then be
applied with:

```bash
docker run --rm -v $PWD:/working gcr.io/k8s-prow/peribolos --config-path /working/config.yaml --github-token-path /working/.access-token --fix-org-members --confirm
```

### Adding and managing repo configuration

```bash
docker run --rm -v $PWD:/working gcr.io/k8s-prow/peribolos --config-path /working/config.yaml --github-token-path /working/.access-token --fix-repos --fix-team-repos --confirm
```

### Adding/removing teams and team members

```bash
docker run --rm -v $PWD:/working gcr.io/k8s-prow/peribolos --config-path /working/config.yaml --github-token-path /working/.access-token --fix-teams --fix-team-members --confirm
```
