# Peribolos configuration for managing the stephengrier-org GitHub organisation

Peribolos can generate an initial configuration for an existing GitHub
organisation like so:

```bash
docker run --rm -v $PWD:/working gcr.io/k8s-prow/peribolos --dump stephengrier-org --dump-full --github-token-path /working/.access-token | tee ./config.yaml
```

## Deploying changes

Configuration changes can be applied like so:

```bash
docker run --rm -v $PWD:/working gcr.io/k8s-prow/peribolos --config-path /working/config.yaml --github-token-path /working/.access-token --fix-org
```

