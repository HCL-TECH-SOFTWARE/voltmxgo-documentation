# Connect to Domino server from your Notes client

## About this procedure

The procedure guides you in connecting to the Domino server from your Notes client. If you installed Domino using the MXGO Domino Helm chart [](../tutorials/downloadhelmchart.md#1-download-the-domino-rest-api-helm-chart) you should configure a Server Connection document to enable connecting to Domino from your Notes client. Follow the steps below.

## Before you start

Make sure that your `/etc/hosts` file has the preview hostnames. You will need these same entries on any machine you want to connect from, such as your dev laptop. For more information, check the details on [adding preview hostnames](../tutorials/prereq.md#4-add-preview-hostnames).

## Procedure

!!!note
    The procedure is based on using HCL Notes v12.

1. Run the following command to copy the `admin.id` from the domino-drapi pod:

    ```
    kubectl cp -n mxgo -c restapi-log $POD_NAME:/local/notesdata/admin.id ./k8s-notes-admin.id
    ```

    !!!tip
        The `$POD_NAME` in the command represents the name of the Domino pod. To get the name of the Domino pod, run the command `kubectl get pods -n mxgo`. In the following example result, the highlighted text corresponds to the Domino pod name.

        ![Domino pod name](../assets/images/podnamesample.png)

        So using the example result, the command above should look like:

        `kubectl cp -n mxgo -c restapi-log domino-drapi-6989796bdc-nnmdg:/local/notesdata/admin.id ./k8s-notes-admin.id`

        !!!note
            You may see a warning about "Removing leading '/' from member names" which is typical when specifying full paths in the copy command.  Ignore the warning.

    **If necessary, copy the `k8s-notes-admin.id` file to your laptop**.

2. Switch your ID within the Notes client.

    1. On your Notes client, select **File** &rarr; **Security** &rarr; **Switch ID**.
    2. On the **Choose User ID to Switch To** dialog, search and select the `k8s-notes-admin.id` file, and then click **Open**.

        !!!note
            The default password is `password`.


3. Specify your `names.nsf` file within the Notes client.

    1. On the Notes client, select **File** &rarr; **Open** &rarr; **HCL Notes Application**.
    2. On the **Open Application dialog**, search and select the `names.nsf` file, and then click **Open**.

4. Create a new server connection.

    1. On the Notes client, select **Advanced** &rarr; **New** &rarr; **Server Connection**. The **Server Connection** page opens.
    2. On the **Basics** tab, enter `drapi` in the **Server name** text box and then select the **TCPIP** checkbox for **Use LAN port**.
    3. Click the **Advanced** tab, and then enter `drapi.mymxgo.com` for your server in the **Destination server address** text box.

    4. **(Optional)** If you configured the value of the `exposeNRPC` parameter to be `hostPort` during the [DRAPI Helm installation](../tutorials/downloadhelmchart.md), no further configuration is required and you can proceed to **Save & Close**. If instead you specified `nodePort`:

        1. Run the following `kubectl` command to get the port number of the port picked by Kubernetes for the `nodePort`:

            ```text
            kubectl get services domino-drapi-nrpc-external -n mxgo
            ```

            The output should be similar to the following:

            ```{ .yaml .no-copy }
            kubectl get services domino-drapi-nrpc-external -n mxgo
            NAME                         TYPE       CLUSTER-IP     EXTERNAL-IP   PORT(S)
            domino-drapi-nrpc-external   NodePort   10.43.84.236   <none>        1352:31657/TCP
            ```

        2. Get the port number from the output and append it to the host name in the **Destination server address** text box.

            Using the output example, the PORT(S) column show that port 1352 is being exposed on port 31657.  Append `:31657` to the host name in the **Destination server address** text box making a final value of `drapi.mymxgo.com:31657`.

    5. Click **Save & Close**.
    !!!note
        `drapi` is the abbreviation for Domino REST API.

## Expected result

In your Notes client, you should now be able to select **File** &rarr; **Open** &rarr; **HCL Notes Application**, specify `drapi` as the server name, and connect to your new Domino server.


