# Secrets
Secrets are generated with [kubeseal](https://github.com/bitnami-labs/sealed-secrets)
## Prereq
`export KUBECONFIG=/etc/rancher/k3s/k3s.yaml`

## Create secrets as such:
`# echo -n 'secretpass' | kubectl create secret generic homeassistant-auth --dry-run=client --from-file=homeassistant-auth-token=/dev/stdin -o json --namespace monitoring | kubeseal > secrets/sealed-homeassistant-auth.json`
or:
`# kubectl create secret generic authentik --dry-run=client --from-file=AUTHENTIK_REDIS__PASSWORD=.secrets/authentik-cache-pass.key -o json --namespace sso | kubeseal --merge-into authentik/sealed-authentik-auth.json`
