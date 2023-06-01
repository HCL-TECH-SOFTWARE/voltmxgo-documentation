# FAQ and common procedures

!!!note
    You can copy and update the pod names from the code examples. We plan to improve this experience in future updates by adding label support.

- Show the notes that were displayed initially after deploying Domino

    ```
    helm get notes domino
    ```

- View the Domino REST API startup / initialization logs:

    ```
    kubectl logs domino-drapi-784d86bf6b-v6dzt -c drapi | less
    ```

- View the Domino server logs

    ```
    kubectl logs domino-drapi-784d86bf6b-v6dzt -c domino-log | less
    ```

- View the Domino REST API logs

    ```
    kubectl logs domino-drapi-784d86bf6b-v6dzt -c restapi-log | less
    ```

- View all the logs

    ```
    kubectl logs domino-drapi-784d86bf6b-v6dzt --all-containers=true | less
    ```

- Copy a file out of the pod

    ```
    kubectl cp -n mxgo -c restapi-log $POD_NAME:/local/notesdata/admin.id ./admin.id
    ```

- Copy a directory out of the pod

    ```
    kubectl cp -n mxgo -c restapi-log $POD_NAME:/local/notesdata/IBM_TECHNICAL_SUPPORT support/
    ```