<!--# Complete preparatory procedure for first time installation of Volt MX Go-->
# Complete preparatory procedure for moving from Early Access release version to GA release version of Volt MX Go

--8<-- "devtestenvironment.md"

The following procedure must be performed if you participated in the Early Access program, and you are moving from the EA release version to the GA release version, as there is no upgrade mechanism.

## 1. Configure Helm to pull from HCL Container Repository

The procedure sets up Helm with the details necessary to authenticate with the HCL Container Repository. You will need your [email and authentication token](obtainauthenticationtoken.md) used with the HCL Container Repository. The GA release of Volt MX Go uses a different repository than the EA release, and the helm commands have been updated to pull from the correct repository.

- Run the following command to properly set up Helm:

    ```
    helm repo remove hclcr
    helm repo add hclcr https://hclcr.io/chartrepo/voltmxgo --username <your hclcr username> --password <your hclcr password>
    ```

    !!!example
         `helm repo remove hclcr`
         `helm repo add hclcr https://hclcr.io/chartrepo/voltmxgo --username user.name@example.com --password xx3ds2w`

    !!!note
        Use the **CLI secret** value you saved from [obtaining authentication token from HCL Container Repository](obtainauthenticationtoken.md) as your authentication token or password.

If you get an error message similar to the following:

``` { .yaml .no-copy }
Error: looks like https://hclcr.io/chartrepo/voltmxgo is not a valid chart repository or cannot be reached: failed to fetch https://hclcr.io/chartrepo/voltmxgo/index.yaml : 401 Unauthorized
```

Most likely, you haven't specified your username or authentication token correctly. Make sure the case and content matches exactly what's listed on the HCL Container Repository site and retry.

## 2. Delete the existing namespace for MXGO EA

Deleting a namespace will remove all of the installed artifacts in that namespace. Run the following command to delete the existing EA namespace:

```
kubectl delete namespace mxgo
```

## 3. Create a namespace for MXGO GA

Run the following commands to create a namespace and set the current context to **mxgo**:

```
kubectl create namespace mxgo
kubectl config set-context --current --namespace=mxgo
```

## 4. Ensure Foundry Hostnames are resolvable

!!!note
    If you are using the same hostnames for GA as you configured for EA, and your IP address hasn't changed, you can skip this step.

You must ensure the url used to access Foundry and Domino REST API are resolvable by all systems that will be accessing it including Kubernetes and any browsers that you use. This can be done by adding DNS host names and IP addresses to your corporate DNS configuration, or by modifying the hosts file for all systems.

In the examples that follow you're going to use these hostnames as examples:

```
drapi.mymxgo.com - used to access Domino REST API.
drapi-management.mymxgo.com - used to access the Domino REST API Management interface.
foundry.mymxgo.com - used to access HCL Volt MX Foundry
```

You can either provide your own hostnames, or use these example names. Either the name to IP address mapping must be made in your DNS configuration, or you must modify your system hosts file. Further documentation here assumes you aren't using a DNS system and configuration and are therefore modifying local hosts file entries.

!!!tip
    Obtain your machine's IP ADDRESS as you will need it in the following step.

Add the hostnames that you have chosen to use in your `/etc/hosts` file together with your **IP ADDRESS** and **dns domain name**. As an example:

```
10.190.252.181 drapi.mymxgo.com drapi-management.mymxgo.com foundry.mymxgo.com
```

!!!note
    If you will be accessing this deployment from other remote machines, you need to apply this same `/etc/hosts` file change on those machines as well.

### For K3s only

!!!note
    If you are using the same hostnames for GA as you configured for EA, and your IP address hasn't changed, you can skip this step.

1. Run the following command to make these name/IP address matches available within the Kubernetes:

    ```
    kubectl edit configmap -n kube-system coredns
    ```

2. Locate the segment that looks like the following:

    ``` { .yaml .no-copy }
        import /etc/coredns/custom/*.server
      NodeHosts: |
        10.190.252.181 vm1.example.com
    kind: ConfigMap
    ```

3. Before the line that starts with `kind: ConfigMap`, add a new line that uses the same IP address, but adds the hostnames you have chosen to use. When done, the segment of the file looks like the following code, but with your IP address and your own hostname. The previously hard-coded values are shown in this example:

    ```{ .yaml .no-copy }
        import /etc/coredns/custom/*.server
      NodeHosts: |
        10.190.252.181 vm1.example.com
        10.190.252.181 drapi.mymxgo.com drapi-management.mymxgo.com foundry.mymxgo.com
    kind: ConfigMap
    ```

4. Save the file and exit the editor.
5. Run the following command to force the restart of the coredns pod:

    ```
    kubectl delete pod -n kube-system -l k8s-app=kube-dns
    ```

### For Rancher Desktop only

You must restart Rancher Desktop:

1. Select **File** &rarr; **Exit** to close the current session.
2. Open a new session by opening Rancher Desktop via the desktop icon.

## 5. Remove the temp directory for the EA charts

!!!note
    You may want to create a backup copy of the `~/mxgo/drapi/values.yaml` and `~/mxgo/foundry/values.yaml` files so you can reuse the settings from them if you are using the same information such as hostnames, userids, and passwords.

Run the following command to remove the temp directory for the EA charts:

```
rm -rf ~/mxgo
```

## 6. Create a temp directory for the GA charts

Run the following commands to create a temp directory for the charts and make it the current directory:

```
mkdir ~/mxgo
cd ~/mxgo
```

## Next step

Proceed to [Install Domino REST API](downloadhelmchart.md).