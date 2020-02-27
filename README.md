# kubernetes-examples
learning k8s

# kustomize

brew install kustomize

# example of kustomize

    mkdir -p base
    BASE=base
    CONTENT="https://raw.githubusercontent.com/kubernetes-sigs/kustomize/master/examples/ldap"
    curl -s -o "$BASE/#1" "$CONTENT/base/{deployment.yaml,kustomization.yaml,service.yaml,env.startup.txt}"

    mkdir -p overlays/dev
    OVERLAYS=overlays
    curl -s -o "$OVERLAYS/dev/#1" "$CONTENT/overlays/staging/{config.env,deployment.yaml,kustomization.yaml}"

    mkdir -p overlays/production
    curl -s -o "$OVERLAYS/production/#1" "$CONTENT/overlays/production/{deployment.yaml,kustomization.yaml}"

## kustomize commands

    kustomize build $BASE
    kustomize build $BASE | kubectl apply -f -

    kustomize build $OVERLAYS/dev
    kustomize build $OVERLAYS/dev | kubectl apply -f -

    kustomize build $OVERLAYS/production
    kustomize build $OVERLAYS/production | kubectl apply -f -

    diff  <(kustomize build $OVERLAYS/dev) <(kustomize build $OVERLAYS/production) | more
