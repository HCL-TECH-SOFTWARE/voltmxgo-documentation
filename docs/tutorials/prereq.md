# Prerequisite procedures

The following procedures must be performed post installation of K3s or Rancher Desktop, and before the download of the Domino/Keep Helm chart and Foundry installation. 

## 1. Configure Helm to pull from HCL Container Repository

The procedure sets up Helm with the details necessary to authenticate with the HCL Container Repository. You will need your [email and authentication token](k3sinstall.md#5-obtain-your-authentication-token-from-hcl-container-repository) used with the HCL Container Repository.

1. Run the following command to set up Helm:

    ```
    helm repo add hclcr https://hclcr.io/chartrepo/voltmxgo  --username $HCLCR_USERNAME
    ```

2. When prompted for a password, enter your authentication token for HCL Container Repository.  

If you get an error message similar to the following:

```
https://hclcr.io/chartrepo/voltmxgo is not a valid chart repository or cannot be reached: 
```

```
failed to fetch https://hclcr.io/chartrepo/voltmxgo/index.yaml : 401 Unauthorized
```

Most likely, you haven't specified your username or authentication token correctly. Make sure the case and content matches exactly what's listed on the HCL Container Repository site and retry.

## 2. Create a namespace for MXGO

- Run the following commands to create a namespace and set the current context to **mxgo**:

    ```
    kubectl create namespace mxgo
    kubectl config set-context --current --namespace=mxgo
    ```

## 3. Add Early Access Preview Host Names

For the Early Access preview, the following host names are **hard-coded**:

```
drapi.mymxgo.com
drapi-management.mymxgo.com
foundry.mymxgo.com
```

- Run the following command to add these host names in your `/etc/hosts` file to your **IP ADDRESS** and **dns domain name**:

    ```
    10.190.252.181 drapi.mymxgo.com drapi-management.mymxgo.com foundry.mymxgo.com
    ```

!!!note
    If you will be accessing this deployment from other remote machines you will need to apply this same `/etc/hosts` file change on those machines as well.

### For K3s only

1. Run the following command to make these name/IP address matches available within the Kubernetes: 

    ```
    kubectl edit configmap -n kube-system coredns
    ```

2. Locate the segment that looks like following:

    ```
        import /etc/coredns/custom/*.server
      NodeHosts: |
        10.190.252.181 vm1.example.com
    kind: ConfigMap
    ```

3. Before the line that starts with `kind: ConfigMap`, add a new line that uses the same IP address, but adds the hard-coded host names. When done, the segment of the file looks like the following, but with your IP address and your own host name:

    ```
        import /etc/coredns/custom/*.server
      NodeHosts: |
        10.190.252.181 vm1.example.com
        10.190.252.181 drapi.mymxgo.com drapi-management.mymxgo.com foundry.mymxgo.com
    kind: ConfigMap
    ```
4. Save the file and exit the editor.


## 4. Create a temp directory for the charts

- Run the following commands to create a temp directory for the charts and make it the current directory:

    ```
    mkdir ~/mxgo
    cd ~/mxgo
    ```

## 5. Setup Helm with credentials

1. Run the following command to setup Helm with credentials:

    ```
    helm repo add hclcr https://hclcr.io/chartrepo/voltmxgo --username $HCLCR_USERNAME
    ```

2. When prompted for a password, enter your authentication token for HCL Container Repository.

## Next step

Proceed to [Download Domino/Keep Helm chart](downloadhelmchart.md).