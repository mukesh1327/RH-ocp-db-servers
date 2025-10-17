# Databases in OCP

Note: Role binding with SCC in manifests are only for Openshift and not for K8s

## 1. Postgres SQL

Deploy as statefulset

```shell script
oc create -f postgresql -n project_name
```

<!-- Test the connection

```shell script
oc run -i --rm postgresdb-test --image=registry.redhat.io/rhel9/postgresql-16 --restart=Never   --tty -- /bin/bash
``` -->

Delete deployed server

```shell script
oc delete -f postgresql -n project_name

# check pvc is delete

oc get pvc

oc delete pvc pvc_name

# or delete each resource individually from CLI or Console
```


## 2. Microsoft SQL

Image is avaiable in [Red Hat container catalog](https://catalog.redhat.com/en/software/containers/mssql/rhel/server/61f2f612f385723914ed60bc).  
For more info: [Doc](https://learn.microsoft.com/en-us/sql/linux/sql-server-linux-docker-container-deployment?view=sql-server-ver17&pivots=cs1-bash#run-rhel-based-container-images) 

Deploy as statefulset

```shell script
oc create -f mssql -n project_name
```

<!-- Test the connection

```shell script
oc run -i --rm mssqldb-test --image=mcr.microsoft.com/mssql/server:2022-latest --restart=Never --tty -- /bin/sh
``` -->

Delete deployed server

```shell script
oc delete -f mssql -n project_name


# check pvc is delete

oc get pvc

oc delete pvc pvc_name

# or delete each resource individually from CLI or Console
```
