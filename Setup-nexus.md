### Starting Nexus Repostory Manager Within OpenShift Cluster

### 1. oc new-project nexus

### 2. oc new-app sonatype/nexus:oss

### 3. oc expose svc/nexus
```
--> Found container image a914737 (11 days old) from Docker Hub for "sonatype/nexus:oss"

    Red Hat Universal Base Image 7 
    ------------------------------ 
    The Universal Base Image is designed and engineered to be the base layer for all of your containerized applications, middleware and utilities. This base image is freely redistributable, but Red Hat only supports Red Hat technologies through subscriptions for Red Hat products. This image is maintained by Red Hat and updated regularly.

    Tags: base rhel7

    * An image stream tag will be created as "nexus:oss" that will track this image

--> Creating resources ...
    imagestream.image.openshift.io "nexus" created
    deployment.apps "nexus" created
    service "nexus" created
--> Success
    Application is not exposed. You can expose services to the outside world by executing one or more of the commands below:
     'oc expose service/nexus' 
    Run 'oc status' to view your app.
 ```
 
 ### 4. oc project nexus
 ### 5. oc get all
 ```
 NAME                         READY   STATUS    RESTARTS   AGE
pod/nexus-5db7c57f99-mgt8p   1/1     Running   0          42s

NAME            TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)    AGE
service/nexus   ClusterIP   172.30.162.14   <none>        8081/TCP   43s

NAME                    READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/nexus   1/1     1            1           44s

NAME                               DESIRED   CURRENT   READY   AGE
replicaset.apps/nexus-5db7c57f99   1         1         1       43s
replicaset.apps/nexus-789bbc8c5b   0         0         0       44s

NAME                                   IMAGE REPOSITORY                                                                  TAGS   UPDATED
imagestream.image.openshift.io/nexus   default-route-openshift-image-registry.apps.lxmlops.cp.fyre.ibm.com/nexus/nexus   oss    43 seconds ago

NAME                             HOST/PORT                                  PATH   SERVICES   PORT       TERMINATION   WILDCARD
route.route.openshift.io/nexus   nexus-nexus.apps.lxmlops.cp.fyre.ibm.com          nexus      8081-tcp                 None

```

### 6.0 oc get is

```
NAME    IMAGE REPOSITORY                                                                  TAGS   UPDATED
nexus   default-route-openshift-image-registry.apps.lxmlops.cp.fyre.ibm.com/nexus/nexus   oss    2 minutes ago
```


### 7.0 oc get pods
```
NAME                     READY   STATUS    RESTARTS   AGE
nexus-5db7c57f99-mgt8p   1/1     Running   0          3m58s
```

### 8.0 oc get routes
```
NAME    HOST/PORT                                  PATH   SERVICES   PORT       TERMINATION   WILDCARD
nexus   nexus-nexus.apps.lxmlops.cp.fyre.ibm.com          nexus      8081-tcp                 None
```

### 9.0 Accessing the Repository Manager

![Nexus](https://github.com/ekambaraml/openshift-nexus/blob/main/Screen%20Shot%202021-12-29%20at%2012.41.07%20PM.png)

