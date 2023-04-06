# Kubernetes cheat sheet

- To show the notes that were displayed initially after deploying Domino:

`helm get notes domino`

- To view the Domino startup / initialization logs:

`kubectl logs domino-keep-784d86bf6b-v6dzt -c qs-keep | less`

- To view the Domino server logs

`kubectl logs domino-keep-784d86bf6b-v6dzt -c domino-log | less`

- To view the REST API logs

`kubectl logs domino-keep-784d86bf6b-v6dzt -c restapi-log | less`

- To view all of the logs

`kubectl logs domino-keep-784d86bf6b-v6dzt --all-containers=true | less`

- To copy a file out of the pod

`kubectl cp -n mxgo -c restapi-log $POD_NAME:/local/notesdata/admin.id ./admin.id`

- To copy a directory out of the pod

`kubectl cp -n mxgo -c restapi-log $POD_NAME:/local/notesdata/IBM_TECHNICAL_SUPPORT support/`