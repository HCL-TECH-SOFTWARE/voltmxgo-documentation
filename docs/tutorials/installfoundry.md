# Install Foundry

The procedures will guide you in the installation of Foundry. 

## 1. Download Foundry charts

1. Run the following commands to download the Foundry charts, unpack the files, and move the `values.yaml` file to the current directory:

    ```
    helm pull hclcr/voltmx-dbupdate
    helm pull hclcr/voltmx-foundry
    tar -xzf voltmx-foundry-1.1.0.tgz
    tar -xzf voltmx-dbupdate-1.1.0.tgz
    mv voltmx-foundry/values.yaml  ./
    ```

2. Edit the `values.yaml` file to update the `imageCredentials` by replacing `your-email` and   `your-authentication-token` with your [email and authentication token](k3sinstall.md#5-obtain-your-authentication-token-from-hcl-container-repository) used with the HCL Container Repository.

    ```
    imageCredentials:
      username: your-email
      password: your-authentication-token
    ```

3. Save the file and exit.

## 2. Deploy Foundry's dbupdate to create the databases in MySql

1. Run the following Helm install command to deploy Foundry's dbupdate:

    ```
    helm install dbupdate voltmx-dbupdate -f values.yaml
    ```

2. Run the following command to verify deployment completion of Foundry's dbupdate:

    ```
    kubectl get pods -o wide -w
    ```

    The output should be similar to the following and will update over time:

```
NAME    READY   STATUS    RESTARTS   AGE   IP      NODE              NOMINATED NODE   READINESS GATES
domino-keep-5c65d76c6c-rkfml  3/3     Running   0 23m   10.42.0.13   k3s.fnxlabs.com<none>           <none>
mysql-0                           1/1     Running   0          12m   10.42.0.15   k3s.fnxlabs.com   <none>           <none>
foundry-db-update-5c56h           1/1     Running   0          65s   10.42.0.17   k3s.fnxlabs.com   <none>           <none>
foundry-db-update-5c56h           0/1     Completed 0          2m37s 10.42.0.17   k3s.fnxlabs.com   <none>           <none>
foundry-db-update-5c56h           0/1     Completed 0          2m39s 10.42.0.17   k3s.fnxlabs.com   <none>           <none>
foundry-db-update-5c56h           0/1     Completed 0          2m40s 10.42.0.17   k3s.fnxlabs.com   <none>           <none>
```

Once the dbupdate pod shows Completed in the STATUS column, press `Ctrl-c` to stop the command.

## 3. Install Foundry

1. Run the following Helm install command to deploy Foundry:

    ```
    helm install foundry voltmx-foundry -f values.yaml
    ```

2. Run the following command to verify when the Foundry install is ready:

    ```
    kubectl get pods -o wide -w
    ```

You should see an output similar to the following:

```
NAME                                          READY   STATUS              RESTARTS   AGE     IP           NODE              NOMINATED NODE   READINESS GATES
domino-keep-5c65d76c6c-rkfml                  3/3     Running             0          27m     10.42.0.13   k3s.fnxlabs.com   <none>           <none>
mysql-0                                       1/1     Running             0          16m     10.42.0.15   k3s.fnxlabs.com   <none>           <none>
foundry-db-update-5c56h                       0/1     Completed           0          5m31s   10.42.0.17   k3s.fnxlabs.com   <none>           <none>
voltmx-foundry-apiportal-64fd9ccb7d-gr2xc     0/1     ContainerCreating   0          39s     <none>       k3s.fnxlabs.com   <none>           <none>
voltmx-foundry-console-774f88ff7f-8mz99       0/1     ContainerCreating   0          39s     <none>       k3s.fnxlabs.com   <none>           <none>
voltmx-foundry-engagement-fd5ff95dd-6gvdp     0/1     ContainerCreating   0          39s     <none>       k3s.fnxlabs.com   <none>           <none>
voltmx-foundry-integration-7bd767d54b-mpbwc   0/1     ContainerCreating   0          39s     <none>       k3s.fnxlabs.com   <none>           <none>
voltmx-foundry-identity-f8bf9784b-jg2jw       0/1     ContainerCreating   0          39s     <none>       k3s.fnxlabs.com   <none>           <none>
voltmx-foundry-integration-7bd767d54b-mpbwc   0/1     Running             0          69s     10.42.0.18   k3s.fnxlabs.com   <none>           <none>
voltmx-foundry-apiportal-64fd9ccb7d-gr2xc     0/1     Running             0          75s     10.42.0.21   k3s.fnxlabs.com   <none>           <none>
voltmx-foundry-identity-f8bf9784b-jg2jw       0/1     Running             0          76s     10.42.0.19   k3s.fnxlabs.com   <none>           <none>
voltmx-foundry-engagement-fd5ff95dd-6gvdp     0/1     Running             0          84s     10.42.0.20   k3s.fnxlabs.com   <none>           <none>
voltmx-foundry-console-774f88ff7f-8mz99       0/1     Running             0          96s     10.42.0.22   k3s.fnxlabs.com   <none>           <none>
voltmx-foundry-apiportal-64fd9ccb7d-gr2xc     1/1     Running             0          2m1s    10.42.0.21   k3s.fnxlabs.com   <none>           <none>
voltmx-foundry-identity-f8bf9784b-jg2jw       1/1     Running             0          2m6s    10.42.0.19   k3s.fnxlabs.com   <none>           <none>
voltmx-foundry-integration-7bd767d54b-mpbwc   1/1     Running             0          2m6s    10.42.0.18   k3s.fnxlabs.com   <none>           <none>
voltmx-foundry-engagement-fd5ff95dd-6gvdp     1/1     Running             0          2m14s   10.42.0.20   k3s.fnxlabs.com   <none>           <none>
voltmx-foundry-console-774f88ff7f-8mz99       1/1     Running             0          2m49s   10.42.0.22   k3s.fnxlabs.com   <none>           <none>
```

3. Once all the foundry pods have a 1/1 state in the READY column, press `Ctrl-c` to stop the kubectl command.  


Foundry is now available at [http://foundry.mymxgo.com/mfconsole/](http://foundry.mymxgo.com/mfconsole/).   

!!!note
    If you want to access this deployment from a remote machine, you will most likely need to update the `/etc/hosts` file on the remote machine as well.