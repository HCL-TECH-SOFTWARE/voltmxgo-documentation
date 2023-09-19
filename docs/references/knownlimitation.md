# Known limitations

- Volt MX Go doesn't support the use of the Open API Adapter in the Foundry Integration Services to connect to Domino via Domino REST API. 
- When using helm charts on a supported Kubernetes platform, you must run the `kubectl config set-context --current --namespace=mxgo` command to set the current namespace context and bring up your Ubuntu terminal session after restarting Windows or Rancher Desktop. If you don't run the command after restarting Windows or Rancher Desktop, your kubectl commands might fail.