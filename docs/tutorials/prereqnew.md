# Complete preparatory procedure for upgrading an existing installation of Volt MX Go

--8<-- "devtestenvironment.md"

**The following procedure must be performed when installing a new version of Volt MX Go**. It's assumed that you have already deployed Kubernetes as part of your first installation of Volt MX Go.

!!!warning "Important"
    If you deployed Kubernetes using Rancher Desktop, use an Ubuntu terminal session to run all the commands in this section and the other subsequent sections. To access the Ubuntu terminal, enter "Ubuntu" in the Windows search box and select the Ubuntu for Windows App. An Ubuntu terminal session opens with your home directory set as your current directory.


1.	Run the following command to get a list of pods running Volt MX Go Foundry:

    ```
    kubectl get pods -n mxgo
    ```
    
2.	Run the following to recreate the temporary directory to download the helm charts and make it the current directory:

    **Command:**
    ```
    mkdir ~/<new directory name>
    cd ~/<new directory name>
    ```

    **Example:**
    ```
    mkdir ~/mxgo201
    cd ~/mxgo201
    ```

    In the example above, you create a new directory `mxgo201` that will contain the new helm charts. Creating the new directory allows you to differentiate and compare the helm charts from different MX Go versions.

3. Configure Helm to pull from HCL Container Repository.

    You will need your [email and authentication token](obtainauthenticationtoken.md) used with the HCL Container Repository.

    1. Run the following command to check if `hclcr` is already defined:

        ```
        helm repo list
        ```

    2. If `hclcr` is already defined, proceed to [Next step](#next-step). Otherwise, execute the following step to set up Helm.

        !!!note
            If `hclcr` points to voltmxgo-ea, you should remove it and then proceed to the next step to set up Helm.

    3. Run the following command to set up Helm:

        ```
        helm repo add hclcr https://hclcr.io/chartrepo/voltmxgo --username <your hclcr username> --password <your hclcr password>
        ```

        !!!example
             `helm repo add hclcr https://hclcr.io/chartrepo/voltmxgo --username user.name@example.com --password xx3ds2w`


        !!!note
            Use the **CLI secret** value you saved from [obtaining authentication token from HCL Container Repository](obtainauthenticationtoken.md) as your authentication token or password.

        If you get an error message similar to the following:

        ``` { .yaml .no-copy }
        Error: looks like https://hclcr.io/chartrepo/voltmxgo is not a valid chart repository or cannot be reached: failed to fetch https://hclcr.io/chartrepo/voltmxgo/index.yaml : 401 Unauthorized
        ```

        Most likely, you haven't specified your username or authentication token correctly. Make sure the case and content matches exactly what's listed on the HCL Container Repository site and retry.

## Next step

Proceed to [Upgrade Volt MX Go server components](versionupgrade1.md).


<!--
2.	Run the following command to delete the `mxgo` namespace, which removes all MXGO components and configurations:

    ```
    kubectl delete namespace mxgo
    ```

    !!!note
        Deletion processing time may take a few minutes as Domino, Foundry, MySQL, and associated configurations are being removed.

3.	After completing the namespace deletion, run the following command to make sure the deletion of the namespace:

    ```
    kubectl get all -n mxgo
    ```

	!!!tip
        You'll get the notification `No resources found in mxgo namespace` if the deletion is successful.

4.	Run the following command to delete the directory where you initially pulled the helm charts:

    ```
    rm -rf ~/mxgo/
    ```

    !!!note
        `~/mxgo` is the usual directory where you initially pulled the helm charts. If you used a different directory, replace `~/mxgo` in the command with the directory you used.

5.	Run the following commands to recreate the `mxgo` namespace and set the current context to `mxgo`:

    ```
    kubectl create namespace mxgo
    kubectl config set-context --current --namespace=mxgo
    ```

    --8<-- "restartwindows.md"
-->