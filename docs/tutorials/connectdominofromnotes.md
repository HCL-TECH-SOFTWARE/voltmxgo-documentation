# Connect to Domino server from your Notes client

The procedure guides you in connecting to the Domino server from your Notes client.

## Before you start

Make sure that your `/etc/hosts` file has the early access preview host names. You will need these same entries on any machine you want to connect from, such as your dev laptop. For more information, check the details on [adding early access preview host names](prereq.md#3-add-early-access-preview-host-names). 

## Procedure

1. Run the following command to copy the `admin.id` from the domino/keep pod:

    ```
    kubectl cp -n mxgo -c restapi-log $POD_NAME:/local/notesdata/admin.id ./k8s-notes-admin.id
    ```

    If necessary, copy the `k8s-notes-admin.id` file to your laptop.

2. Switch your ID within the Notes client.

    1. On your Notes client, select **File** &rarr; **Security** &rarr; **Switch ID**.
    2. On the **Choose User ID to Switch To** dialog, search and select the `k8s-notes-admin.id` file, and then click **Open**.

        !!!note
            The default password is `password`.


2. Specify your `names.nsf` file within the Notes client.

    1. On the Notes client, select **File** &rarr; **Application** &rarr; **Open**.
    2. On the **Open Application dialog**, search and select the `names.nsf` file, and then click **Open**.

3. Create a new server connection.

    1. On the Notes client, select **New** &rarr; **Server Connection**. The **Server Connection** page opens.
    2. On the **Basics** tab, enter `keep` in the **Server name** text box and then select the **TCPIP** checkbox for **Use LAN port**. 
    3. Click the **Advanced** tab, and then enter the TCP/IP address for your server in the **Destination server address** text box.
    4. Click **Save & Close**.

## Expected result

In your Notes client, you should now be able to select **File** &rarr; **Application** &rarr; **Open**, specify `keep` as the server name, and connect to your new Domino server.

