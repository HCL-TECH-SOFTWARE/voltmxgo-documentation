# Troubleshooting

List of issues and corresponding resolutions. 

- [**First Touch or Custom Application Fails to Install on Foundry**](https://support.hcltechsw.com/csm?id=kb_article&sysparm_article=KB0106427){: target="_blank"}

    !!!note
        This issue and its corresponding resolution aren't applicable when setting up First Touch in Volt MX Go installed in a development or test-only environment.   

- **The kubectl commands fail after restarting Windows or Rancher Desktop**

    When your kubectl commands fail after restarting Windows or Rancher Desktop, you must run the `kubectl config set-context --current --namespace=mxgo` command in your Ubuntu terminal session to set the current namespace context.