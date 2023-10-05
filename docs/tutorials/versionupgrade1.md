# Upgrade Volt MX Go server components in development or test only environment


## Upgrade Domino REST API

1. Download Domino REST API Helm chart
    1. Run the following command to make sure that the chart information for the repositories is up-to-date. 

        ```
        helm repo update
        ```

        --8<-- "helmversion.md"
     
    2. Run the following command to download the chart:

        ```
        helm pull hclcr/drapi
        ```
        The file `drapi-1.n.n.tgz` is downloaded, wherein `1.n.n` represents the version number such as `1.0.7`.

    3. Run the following commands to unpack the chart and make the DRAPI directory your current directory:

        ```
        tar -xzvf drapi-1.n.n.tgz
        cd drapi
        ```
        !!!note
            The Domino REST API chart name has a version string in the filename. The helm pull command will pull down the latest version of the charts. Ensure your tar command uses the correct matching file names.

2. Update the `values.yaml` file of the target upgrade version with custom settings you want to apply from the `values.yaml` file of your current installation.
3. Within the directory containing the new Domino REST API charts, run the following command:

    ```
    helm upgrade domino . -f values.yaml
    ```

    This upgrades the program executables and reuses the existing databases and all the configuration stored on `/local/notesdata` within the Domino container.
    
4. Run the following command to wait for the Domino pod to be running and in the ready state:

    ```
    kubectl get pods -o wide -w
    ```

    !!!note
        The `-w` flag tells the kubectl command to wait, and updates the output over time with any changes.

## Upgrade Volt MX Go Foundry

1. Download Foundry charts.

    1. Run the following command to make sure that the chart information for the repositories is up-to-date.

        ```
        helm repo update
        ```

        --8<-- "helmversion.md"

    2. Run the following commands to download the Foundry charts, unpack the files, and move the `values.yaml` file to the current directory:

        ```
        mkdir foundry
        cd foundry
        helm pull hclcr/voltmx-dbupdate
        helm pull hclcr/voltmx-foundry
        tar -xzf voltmx-foundry-1.n.n.tgz
        tar -xzf voltmx-dbupdate-1.n.n.tgz
        mv voltmx-foundry/values.yaml  ./
        mv voltmx-foundry/init-guids.sh  ./
        chmod +x init-guids.sh
        ```

        !!!note
            The foundry and dbupdate chart names have a version string in the filename. The `helm pull` command will pull down the latest version of the charts. Ensure your tar command uses the correct matching file names.


2. Obtain the `upgrade.properties` file from your prior deployment and copy it into the same directory as your `values.yaml`.
3. Invoke the init-guids script specifying the file path of the prior deployment's `upgrade.properties` by running the following command:

    ```
    ./init-guids.sh --upgrade ./
    ```

--8<-- "verupgrade.md"

## Additional information

After completing the upgrade installation of **Domino REST API** and **Volt MX Go Foundry**, proceed to [Install and upgrade Volt MX Go Iris](installiris.md).
