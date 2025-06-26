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
      server: https://vivek-test.runailabs-cs.com:6443
      certificate-authority-data: LS0tLS1CRUdJTiBDRVJUSUZJQ0FURS0tLS0tCk1JSURCVENDQWUyZ0F3SUJBZ0lJWVd6bnBMWTFLaXN3RFFZSktvWklodmNOQVFFTEJRQXdGVEVUTUJFR0ExVUUKQXhNS2EzVmlaWEp1WlhSbGN6QWVGdzB5TlRBMk1qWXhOelUxTVRSYUZ3MHpOVEEyTWpReE9EQXdNVFJhTUJVeApFekFSQmdOVkJBTVRDbXQxWW1WeWJtVjBaWE13Z2dFaU1BMEdDU3FHU0liM0RRRUJBUVVBQTRJQkR3QXdnZ0VLCkFvSUJBUURpa3BBNUczd0NKajNMa25QOXpNV1dIUHRtSk1KOWJIOEJ0U0N2MFJQc3NZemEvQ00vUFVyVUg4dXUKWXBIYVFIV3NzQkk4NXVzSW5rTjdVa201SDRMQzRJSFBvWDR2c1k4SXF0akxoS1NOUzdnMVlORUdoSDRuSzQ2TQp4MUY0SWFwc0w3VVpHd1VCdE5hY3hvWXcrcjNFeVB5QythL3g5eTloamZXOU9TS0MyZlRyZTBsQTMxeURMZnRHCm9oZHZhVjBVYXBzVndWMWJMUFY2S09ZcTc5dCt6aWZobXFlWjZSdDRFV09ZVW1VZ0RDK0Y5WnR1NWpPbXo5OWUKUStuSDlVN3BMb01QVXV2UG95OXcydk95QW5uS0JLRlhjVzhuRm01KzJxUDNUamdwV0JwYXhNckljUVZhTkZ6dgptT3lyWlJmcUJqWll0VytUR2VxN0VlbXh0YmI5QWdNQkFBR2pXVEJYTUE0R0ExVWREd0VCL3dRRUF3SUNwREFQCkJnTlZIUk1CQWY4RUJUQURBUUgvTUIwR0ExVWREZ1FXQkJRclFyL0lodEo3SFEyWU5GVjBSZXBJQWZ3YVJqQVYKQmdOVkhSRUVEakFNZ2dwcmRXSmxjbTVsZEdWek1BMEdDU3FHU0liM0RRRUJDd1VBQTRJQkFRQXdSQnRKd2ZaRApmMDQ2YWd6Nld5Zk1aamFLZm1kbW41ZlhxSW8rVzk4OXVoZEhFd1dkWENLYS8rR0xXazRMckVGd3J2dzBIbUNqClZHSE5Xc2NlNzRoYjNlcy93cDJPUFpEcGxIS0VTaFBkZXp0UThyaUN6dnBlc0pVaDE2QzdVNUxLcnB1dkx4bDcKQWNDOU90b1B0Zk0rUStmUVJTTk5DdWRyNXo2SzUvV1k5d1J4bHE5U0lMNlZveG9DdmQ0N3hJVGFINmxCZDhTVgpQOXNVNEx2N2ZDdElMOXg2K3IrazFWZXVOb2RhNk1Od1NZbUV6QzlQSnJFK3gyd0Z2dU8wK2VGeUsraENiaFhPCjU0SmRxRjN2T1psbmU2S0psVzIyOTZxaWhESWQ5amZDbC9iODlhbjE4NWlxN0xWS2pMT1A0Rmx2Y0ZIWlJCWjAKaXE4eXE4U1gvRGNyCi0tLS0tRU5EIENFUlRJRklDQVRFLS0tLS0K
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
          idp-issuer-url: https://vivek-test.runailabs-cs.com/auth/realms/runai
          redirect-uri: https://vivek-test.runailabs-cs.com/oauth-code
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
