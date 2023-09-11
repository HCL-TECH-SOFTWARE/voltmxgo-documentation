# Complete preparatory procedure for upgrading an existing installation of Volt MX Go

--8<-- "devtestenvironment.md"

**The following procedure must be performed when installing a new version of Volt MX Go**. It's assumed that you have already deployed Kubernetes as part of your first installation of Volt MX Go.

!!!warning "Important"
    If you deployed Kubernetes using Rancher Desktop, use an Ubuntu terminal session to run all the commands in this section and the other subsequent sections. To access the Ubuntu terminal, enter "Ubuntu" in the Windows search box and select the Ubuntu for Windows App. An Ubuntu terminal session opens with your home directory set as your current directory.


1.	Run the following command to get a list of pods running Foundry:

    ```
    kubectl get pods -n mxgo
    ```

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

6.	Run the following commands to recreate the temporary directory to download the helm charts and make it the current directory:

    ```
    mkdir ~/mxgo
    cd ~/mxgo
    ```

## Next step

Proceed to [Install Domino REST APIs](downloadhelmchart.md).
