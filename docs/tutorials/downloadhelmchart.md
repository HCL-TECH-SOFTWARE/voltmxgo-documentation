# Download Domino/Keep Helm chart

The procedure guides you in downloading the Domino/Keep Helm chart and deploying Domino.

## 1. Donwload the Domino/Keep Helm chart

1. Run the following command to download the chart:

    ```
    helm pull hclcr/keep
    ```

    The file `keep.tgz` is downloaded. 

2. Run the following commands to unpack the chart and make the Keep directory your current directory:

    ```
    tar -xzvf keep-<version>.tgz
    cd keep
    ```

3. Edit the `values.yaml` file using an editor to update the file with your HCL Container Repository credentials. You can use your preferred editor. 

    The example procedure uses **vi** to edit the `values.yaml` file:

    1. Run the following command:

        ```
        vi values.yaml
        ```

    2. Locate the following lines in the file and replace `your-email` and   `your-authentication-token` with your [email and authentication token](k3sinstall.md#5-obtain-your-authentication-token-from-hcl-container-repository) used with the HCL Container Repository:

        ```
        imageCredentials:
            username: your-email
            password: your-authentication-token
        ```

    3. Save the file and exit.  
    
## 2. Deploy Domino 

1. Deploy Domino by running the following Helm install command: 

    ```
    helm install domino . -f values.yaml -n mxgo
    ```

    !!!note
        The images must be pulled. It might take awhile, 90 seconds or longer, for the pod to start.

2. Run the following command to wait for the Domino pod to be running and in the ready state:

    ```
    kubectl get pods -o wide -w
    ```

    !!!note
        The `-w` flag tells the kubectl command to wait, and updates the output over time with any changes.

    Eventually you should see 3/3 in the READY column as shown below:

    ```
    NAME                           READY   STATUS              RESTARTS   AGE
    domino-keep-68596f98fd-bkpdz   0/3     ContainerCreating   0          34s
    domino-keep-68596f98fd-bkpdz   3/3     Running             0          72s
    ```

3. Once you see the READY column showing 3/3, press `Ctrl+c` to cancel the command.

## Next step

Proceed to [Install MySql for Foundry](installmysqlfoundry.md).