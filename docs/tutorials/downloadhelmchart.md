# Install Domino REST API

The procedure guides you in downloading the Domino REST API Helm chart and deploying Domino REST API.

## 1. Download the Domino REST API Helm chart

1. Run the following command to make sure that the chart information for the repositories is up-to-date.

    ```
    helm repo update
    ```

2. Run the following command to download the chart:

    ```
    helm pull hclcr/drapi
    ```
    The file `drapi-n.n.n.tgz` is downloaded.

3. Run the following commands to unpack the chart and make the DRAPI directory your current directory:

    ```
    tar -xzvf drapi-0.3.2.tgz
    cd drapi
    ```

4. Edit the `values.yaml` file using your preferred editor to update the file with your HCL Container Repository credentials, and the DNS name settings.

    1. Locate the following lines in the file and replace `your-email` and `your-authentication-token` with your [email and authentication token](obtainauthenticationtoken.md) used with the HCL Container Repository:

        ```{ .yaml .no-copy }
        imageCredentials:
            username: your-email
            password: your-authentication-token
        ```

    2. Locate the following lines in the file and add your DNS name settings:

        ```{ .yaml .no-copy }
        ingress:
            drapiDnsName:
            drapiManagementDnsName:
        ```

        !!!note
            The default names used in previous Early Access releases were `drapi.mymxgo.com` and `drapi-management.mymxgo.com` respectively.

    2. Save the file and exit.

## 2. Deploy Domino REST API

1. Deploy Domino REST API by running the following Helm install command:

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

    ```{ .yaml .no-copy }
    NAME                           READY   STATUS              RESTARTS   AGE
    domino-drapi-68596f98fd-bkpdz   0/3     ContainerCreating   0          34s
    domino-drapi-68596f98fd-bkpdz   3/3     Running             0          72s
    ```

3. Once you see the READY column showing 3/3, press `Ctrl-c` to cancel the command.

## Next step

Proceed to [Install MySql for Foundry](installmysqlfoundry.md).