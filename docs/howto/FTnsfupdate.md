# Update FirstTouchRecipes.nsf 

--8<-- "devtestenvironment.md"

## About this task 

Guides you in manually updating your Domino container if you obtain a new version of the Notes database *FirstTouchRecipes.nsf*.

## Procedure

1. [Uninstall the First Touch app](uninstallfirsttouch.md) from Volt MX Go Foundry. 
2. Identify the name of the Domino container by running the following command:

    ```
    kubectl get pods -n mxgo
    ```

    You should see an output similar to the following:

    ```{ .yaml .no-copy }
    NAME                                         READY   STATUS      RESTARTS   AGE
    drapi-6949c45b8-wghbz                        3/3     Running     0          8d
    mysql-0                                      1/1     Running     0          8d
    foundry-db-update-zn5vg                      0/1     Completed   0          7d23h
    voltmx-foundry-apiportal-c874cb6d-l2k8h      1/1     Running     0          7d22h
    voltmx-foundry-integration-76dc89b57-qmq2t   1/1     Running     0          7d22h
    voltmx-foundry-identity-85f9854f8b-n6b2d     1/1     Running     0          7d22h
    voltmx-foundry-console-664c75c6b5-8lm6v      1/1     Running     0          7d22h
    ```

    From the example, the name of the Domino pod is `drapi-6949c45b8-wghbz`.

3.  Copy the new `FirstTouchRecipes.nsf` file into the Domino container by running the following:   
    
    Command:

    ```
    kubectl cp FirstTouchRecipes.nsf <Domino pod name>:/tmp/FirstTouchRecipes.nsf -c drapi
    ```

    Example:

    ```{ .yaml .no-copy }
    kubectl cp FirstTouchRecipes.nsf drapi-6949c45b8-wghbz:/tmp/FirstTouchRecipes.nsf -c drapi
    ```

4.  Exec into the Domino container by running the following:

    Command:

    ```
    kubectl exec -it <Domino pod name> -c drapi -- bash
    ```

    Example:

    ```{ .yaml .no-copy }
    kubectl exec -it drapi-6949c45b8-wghbz -c drapi -- bash
    ```

    You should get a shell prompt similar to this:

    ```{ .yaml .no-copy }
    [hcl@drapi-6949c45b8-wghbz ~]$
    ```
    
    !!!warning "Important"
        The succeeding steps involve executing commands from within this container shell. Make sure you run the commands at this new shell prompt. If you get disconnected, run the `kubectl exec -it` command again.

5.  Update your path environment variable by running the following command:

    ```
    export PATH=$PATH:/opt/nashcom/startscript/
    ```

6.  Issue a request to stop Domino by running the following command:

    ```
    rc_domino_script stop
    ```

    You should see something like this for output:

    ```{ .yaml .no-copy }
    Using Domino config File [/etc/sysconfig/rc_domino_config]

    Stopping Domino for xLinux (hcl)
    KEEP started in task mode, no pre_shutdown action required
    ... waiting for shutdown to complete
    ... waiting 10 seconds
    ... waiting 20 seconds
    KEEP started in task mode, no post_shutdown action required
    Domino stopped (27 sec)
    Domino for xLinux (hcl) shutdown completed

    [hcl@drapi-6949c45b8-wghbz ~]$
    ```

7.  Rename original First Touch database and copy in the new database file:

    ```
    mv /local/notesdata/FirstTouchRecipes.nsf  /local/notesdata/FirstTouchRecipes.nsf.original
    ```
    ```
    mv /tmp/FirstTouchRecipes.nsf  /local/notesdata/FirstTouchRecipes.nsf
    ```

8.  Restart Domino by running the following command:
    
    ```
    rc_domino_script start
    ```
    
    The output should indicate:

    ```{ .yaml .no-copy }
    Using Domino config File [/etc/sysconfig/rc_domino_config]


    Archived log file to '/local/notesdata/hcl_231010_182050.log'
    Removed LoadMon-Data '/local/notesdata/loadmon.ncf'

    Starting Domino for xLinux (hcl)
    done PID is 742526

    KEEP starting in task mode, no post_startup action required

    [hcl@drapi-6949c45b8-wghbz ~]$
    ```

You are now set to re-install the First Touch Recipe Catalog application in Volt MX Go Foundry by following the [Log in to Volt MX Go Foundry](../tutorials/firsttouch.md#log-in-to-volt-mx-go-foundry) instructions. 
