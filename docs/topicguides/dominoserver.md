# Interacting with Domino server process within Domino container

Volt MX Go offers a Helm chart to run a Domino server enabled with the Domino REST API (DRAPI) in a Kubernetes environment. This document is meant to offer some guidance and tips on working with the Domino container to get the most out of your Volt MX Go deployment.

## Container basics

When you deploy the Volt MX Go Domino REST API Helm chart, you instruct Kubernetes to create a [pod](https://kubernetes.io/docs/concepts/workloads/pods/){: target="_blank" rel="noopener noreferrer"}<!--that you can think of as a small lightweight Virtual Machine-->. The Helm chart provides the specifics for what program (Image) will run when the pod starts, the details around what ports to expose, such as port 80 for Domino HTTP server, port 8880 for Domino REST API, and the memory and CPU allocations among other things.

The chart also tells Kubernetes about [liveness and readiness probes](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-startup-probes/){: target="_blank" rel="noopener noreferrer"}. Kubernetes runs these probes periodically to determine container health. If a readiness probe fails many times, the container is marked as unready and won't receive any HTTP traffic. If a liveness probe fails many times, Kubernetes assumes the container has unrecoverable errors and then kills and restarts the container. 

These probes are important to understand as some operations require you to stop and restart Domino. If Domino fails to answer liveness probes, such as when Domino is stopped, Kubernetes may remove the container and start a new one. By default, this period is 10 minutes for the Domino container.

The Domino data directory resides in `/local/notesdata` within the Domino container. This directory is actually a mount point for a persistent, initially empty file system created by Kubernetes.

!!!tip
    For more information, see [persistent volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/){: target="_blank" rel="noopener noreferrer"}.

It's used to store the Domino server configuration, Notes databases, templates, and other details specific to the Domino server instance. During initial startup, Domino sees the empty directory and triggers the Domino One Touch setup process to populate the directory with databases, templates, and configuration files. Logs are in `/local/notesdata/IBM_TECHNICAL_SUPPORT/`.

Domino runs under the Unix user ID of `hcl` with primary group of `root`.

## Pod vs Container

A pod and a container are related concepts, but serve different purposes and have distinct characteristics.

**Container**:

- Lightweight, standalone, and executable software package that includes everything needed to run a piece of software, including the code, runtime, system tools, and libraries.
- Provide a consistent and isolated environment for running applications. They're designed to be portable and can run consistently across different environments, such as development, testing, and production.
- Typically, created using containerization technologies like Docker, and they encapsulate individual applications or services.

**Pod**:

- Smallest deployable unit in Kubernetes, which is a container orchestration platform.
- Contains one or more containers that are coupled and share the same network namespace, IPC namespace, and storage volumes.
    
    !!!note
        Containers within the same pod share the same resources and can communicate with each other using localhost, making them suitable for co-locating integrated services.

- Often used to group containers that need to work together, such as a web server and a sidecar for logging.

**Key differences**:

* A container is a single lightweight unit that encapsulates an application and its dependencies.
* A pod is a higher-level concept in Kubernetes and can contain one or more coupled containers scheduled together on the same host.
* Containers package and run individual applications or services, while pods group containers that need to work together and share certain resources.

Kubernetes uses pods as its fundamental scheduling unit because they provide a way to manage co-located containers and offer flexibility for deploying complex applications with multiple services.

## Pod names

Pods have names that usually consist of developer defined prefix and runtime defined unique suffix. Together they make each pod name unique. Because of this, you often have to get a list of the running pods to determine the exact name before taking action on the pod. Use the kubectl command [`get pods`](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#get){: target="_blank" rel="noopener noreferrer"} as shown here:

```{ .yaml .no-copy }
kubectl get pods -n mxgo
```

You should see output similar to this:

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
Locate the entry that starts with "drapi" and you can see the full pod name is **drapi-6949c45b8-wghbz**.

## Copy files into and out of Domino container

Using the [kubectl cp](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#cp){: target="_blank" rel="noopener noreferrer"} command, you can copy files into and out of the container. For example, if you want to copy the domino administrative ID out of the Domino data directory, you use a command like this:

```{ .yaml .no-copy }
kubectl cp voltmxgo-drapi-848d9fc9f9-9vcgf:/local/notesdata/admin.id domino-id.id -n mxgo -c drapi
```

Here, the `cp` command copies the file `/local/notesdata/admin.id` out of the container `voltmxgo-drapi-848d9fc9f9-9vcgf` to the file `domino-id.id` in the current working directory. The flag `-n mxgo` indicates that the Kubernetes namespace is `mxgo` and the flag `-c drapi` indicates using the drapi container within the Domino DRAPI pod.

Similiarly, you could copy the local file `foo.bar` into the container's `/tmp` directory like this:

```{ .yaml .no-copy }
kubectl cp foo.bar  voltmxgo-drapi-848d9fc9f9-9vcgf:/tmp/foo.bar -n mxgo -c drapi
```

Refer to [Kubernetes documentation](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#cp) for more details on `cp`.


## Interactive command line access with Domino

You can get a bash prompt within the Domino container much like when you SSH into a remote Linux host. You do this with the `kubectl exec` command. You may start a bash command session like this:

```{ .yaml .no-copy }
kubectl exec -it voltmxgo-drapi-848d9fc9f9-9vcgf  -n mxgo -c drapi -- bash
```

The response should look like the following, which indicates you are now in a bash shell command prompt within the Domino REST API container:

```{ .yaml .no-copy }
[hcl@voltmxgo-drapi-848d9fc9f9-9vcgf ~]$
```

You can use the nashcom [Domino Start Script](https://nashcom.github.io/domino-startscript/) to interact with the Domino server. This script is already installed and available for use.

First add the program directory `/opt/nashcom/startscript/` to your path:

```{ .yaml .no-copy }
export PATH=$PATH:/opt/nashcom/startscript/
```

You can now show the status of the Domino server by using this command:

```{ .yaml .no-copy }
rc_domino_script status
```

You should see:

```{ .yaml .no-copy }
Domino Server is running (hcl)
```

You can attach to the Domino console with the `live` command and see something like this:

```{ .yaml .no-copy }
[hcl@voltmxgo-drapi-848d9fc9f9-9vcgf ~]$ rc_domino_script live
Using Domino config File [/etc/sysconfig/rc_domino_config]


--- Live Console for hcl ---

To close console, always type 'close' or 'stop'.


[000582:000002-00007FBF5156C740] 10/09/2023 04:39:48 PM  Directory Catalog entitlements.nsf needs rebuilding (Replication to all mobile clients will take longer): Rebuilding due to no replication history
[006013:000002-00007FA7624F1740] 10/09/2023 04:39:48 PM  Chronos: Performing hourly full text indexing
[006013:000002-00007FA7624F1740] 10/09/2023 04:39:55 PM  Chronos: Full text indexer terminating
[000588:000002-00007FF2B92FC740] 10/09/2023 04:45:42 PM  Admin Process: Searching Administration Requests database
[009792:000002-00007F0024E1A740] 10/09/2023 05:39:53 PM  Chronos: Performing hourly full text indexing
[009792:000002-00007F0024E1A740] 10/09/2023 05:39:59 PM  Chronos: Full text indexer terminating
[000588:000002-00007FF2B92FC740] 10/09/2023 05:45:41 PM  Admin Process: Searching Administration Requests database
[013563:000002-00007FF34BA4B740] 10/09/2023 06:39:53 PM  Chronos: Performing hourly full text indexing
[013563:000002-00007FF34BA4B740] 10/09/2023 06:39:59 PM  Chronos: Full text indexer terminating
[000588:000002-00007FF2B92FC740] 10/09/2023 06:45:42 PM  Admin Process: Searching Administration Requests database
```

Once in the console, you can run other Domino console command such as `show tasks`:

```{ .yaml .no-copy }
show tasks


[000191:000015-00007FEDB3E7C700]       Task                 Description
[000191:000015-00007FEDB3E7C700]  Database Server      Perform console commands
[000191:000015-00007FEDB3E7C700]  Database Server      Listen for connect requests on TCPIP
[000191:000015-00007FEDB3E7C700]  Database Server      Load Monitor is idle
[000191:000015-00007FEDB3E7C700]  Database Server      Database Directory Manager Cache Refresher is idle
[000191:000015-00007FEDB3E7C700]  Database Server      Organization Name Cache Refresher is idle
[000191:000015-00007FEDB3E7C700]  Database Server      Log Purge Task is idle
[000191:000015-00007FEDB3E7C700]  Database Server      Idle task
[000191:000015-00007FEDB3E7C700]  Database Server      Idle task
[000191:000015-00007FEDB3E7C700]  Database Server      log.nsf Commit Thread
[000191:000015-00007FEDB3E7C700]  Database Server      Perform Database Cache maintenance
[000191:000015-00007FEDB3E7C700]  Database Server      Idle task
[000191:000015-00007FEDB3E7C700]  Database Server      Platform Stats is idle
[000191:000015-00007FEDB3E7C700]  Database Server      Metric Task
[000191:000015-00007FEDB3E7C700]  Database Server      Shutdown Monitor
[000191:000015-00007FEDB3E7C700]  Database Server      Process Monitor
[000191:000015-00007FEDB3E7C700]  LDAP Server          Listen for connect requests on TCP Port:389
[000191:000015-00007FEDB3E7C700]  LDAP Server          Utility task
[000191:000015-00007FEDB3E7C700]  Router               Utility: Idle
[000191:000015-00007FEDB3E7C700]  Router               MailEvent: Idle
[000191:000015-00007FEDB3E7C700]  Router               Dispatch: Idle
[000191:000015-00007FEDB3E7C700]  Router               Dispatch: Idle
[000191:000015-00007FEDB3E7C700]  Agent Manager        Executive '1': Idle
```

Experienced Domino administrators know that sometimes you must run a process called `fixup` to fix a corrupt database. You can do this from here using the following command:

```
Load fixup <databasepath> <options>
```

You may disconnect from the console, and leave the Domino Server running, using the command `close`.

For the full set of server commands and syntax, see the [HCL Domino Documentation](https://help.hcltechsw.com/domino/12.0.0/admin/admn_servercommandsyntax_c.html){: target="_blank" rel="noopener noreferrer"}.

## Stop and start Domino server process

If you need to stop and restart the Domino server without killing the entire pod, you may exec into the Domino pod and issue the command to stop and then restart Domino. Here is an example with a typical output:

```{ .yaml .no-copy }
kubectl exec -it voltmxgo-drapi-848d9fc9f9-9vcgf  -n voltmxgo -c drapi -- bash
[hcl@voltmxgo-drapi-848d9fc9f9-9vcgf ~]$ export PATH=$PATH:/opt/nashcom/startscript/
[hcl@voltmxgo-drapi-848d9fc9f9-9vcgf ~]$ rc_domino_script stop
Using Domino config File [/etc/sysconfig/rc_domino_config]

Stopping Domino for xLinux (hcl)
KEEP started in task mode, no pre_shutdown action required
 ... waiting for shutdown to complete
 ... waiting 10 seconds
 ... waiting 20 seconds
KEEP started in task mode, no post_shutdown action required
Domino stopped (26 sec)
Domino for xLinux (hcl) shutdown completed
```

Restart using the `start` command:

```{ .yaml .no-copy }
[hcl@voltmxgo-drapi-848d9fc9f9-9vcgf ~]$ rc_domino_script start
Using Domino config File [/etc/sysconfig/rc_domino_config]


Archived log file to '/local/notesdata/hcl_231009_193905.log'
Removed LoadMon-Data '/local/notesdata/loadmon.ncf'

Starting Domino for xLinux (hcl)
done PID is 20210

KEEP starting in task mode, no post_startup action required

[hcl@voltmxgo-drapi-848d9fc9f9-9vcgf ~]$
```

You can also use the `restart` command.

!!!warning "Important"
    If you leave Domino stopped for too long, usually longer than 10 minutes, Kubernetes liveness tests detect this and may delete the pod and restart a new one.