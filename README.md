# Researcher Kubeconfig Setup Guide

## Step 1: Save Kubeconfig File

Save the following configuration as `~/.kube/config`:

```yaml
apiVersion: v1
kind: Config
preferences:
  colors: true
current-context: vivek-test
contexts:
  - context:
      cluster: vivek-test
      user: runai-authenticated-user
    name: vivek-test
clusters:
  - cluster:
      server: https://vivek-test.com:6443
      certificate-authority-data: xxxxxx
    name: vivek-test
users:
  - name: runai-authenticated-user
    user:
      auth-provider:
        config:
          airgapped: "true"
          auth-flow: remote-browser
          realm: runai
          client-id: runai-cli
          idp-issuer-url: https://vivek-test.com/auth/realms/runai
          redirect-uri: https://vivek-test.com/oauth-code
        name: oidc
```

## Step 2: Install Run:ai CLI

Login to runai and install the runai CLI using your researcher account.

## Step 3: Authenticate

Once it is installed, do a runai login:
```bash
runai login
```
This will open a browser window for authentication.

## Step 4: Configure Kubeconfig

Configure kubeconfig with Run:ai token:
```bash
runai kubeconfig set
```

## Step 5: Verify Connection

Verify the connection:
```bash
kubectl get pods -n runai-project
```
