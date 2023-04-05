# Install MySql for Foundry

The procedure guides you in installing MySql for Foundry.

1. Run the following commands to create a Foundry directory in the proper location, and and make the Foundry directory the current directory:

    ```
    cd ..
    mkdir foundry
    cd foundry
    ```

2. Run the following commands to install the Bitnami MySql Helm chart to use for the Foundry database storage:

    ```
    helm repo add bitnami https://charts.bitnami.com/bitnami
    helm install mysql bitnami/mysql --version "9.6.0" --set image.tag="8.0.32-debian-11-r17",auth.rootPassword="Password123\!",auth.createDatabase=false,auth.username=dbclient,auth.password="Password123\!" -n mxgo
    ```

3. Run the following command to verify when the database is in the ready state:

    ```
    kubectl get pods -o wide -w
    ```

    mysql-0 should show 1/1 in the READY column as shown in the following output example to indicate that the database is in the ready state.

    ```
    NAME                              READY   STATUS    RESTARTS   AGE
    domino-keep-5c65d76c6c-rkfml      3/3     Running   0          11m
    mysql-0                           1/1     Running   0          45s
    ```

4. Once the database is in the ready state, press `Ctrl-c` to stop the command.