4. Update the `values.yaml` file of the target upgrade version with custom settings you want to apply from the `values.yaml` file of your current installation.
5. Remove the dbupdate deployment by running the following command:

    ```
    helm uninstall dbupdate -n mxgo
    ```

6. Scale down existing Volt Foundry deployments to zero by running the following commands:

    ```
    kubectl scale deployment --replicas=0 voltmx-foundry-console
    kubectl scale deployment --replicas=0 voltmx-foundry-apiportal
    kubectl scale deployment --replicas=0 voltmx-foundry-integration
    kubectl scale deployment --replicas=0 voltmx-foundry-identity
    ```

7. Confirm that the ready count has dropped to zero by running the following command:

    ```
    kubectl get deployment
    ```

    You should get an output similar to the following where the ready count has dropped to zero:

    ```{ .yaml .no-copy }
    NAME                         READY   UP-TO-DATE   AVAILABLE   AGE
    drapi                        1/1     1            1           5h40m
    voltmx-foundry-console       0/0     0            0           51m
    voltmx-foundry-identity      0/0     0            0           51m
    voltmx-foundry-integration   0/0     0            0           51m
    voltmx-foundry-apiportal     0/0     0            0           51m
    ```

8. Confirm the removal of the pods by running the following command:

    ```
    kubectl get pods
    ```

    You should get an output similar to the following where the Volt Foundry pods have been removed:

    ```{ .yaml .no-copy}
    NAME                      READY   STATUS      RESTARTS   AGE
    drapi-6949c45b8-wghbz     3/3     Running     0          5h40m
    mysql-0                   1/1     Running     0          5h36m
    ```

9. Upgrade the Volt Foundry applications by running the following command:

    ```
    helm upgrade foundry voltmx-foundry -f values.yaml
    ```

    This updates the deployment configuration and spins up new pods to run the latest version of the applications.