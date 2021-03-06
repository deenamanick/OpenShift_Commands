To Find out resource limit for the Project

```
oc get limits -n ProjectName

sample output

[xxxx@xxxx ~]$ oc describe limits core-resource-limits -n NAMESPACE
Name:                           core-resource-limits
Namespace:                      APPS NAMESPACE
Type                            Resource                Min     Max     Default Request Default Limit   Max Limit/Request Ratio
----                            --------                ---     ---     --------------- -------------   -----------------------
Pod                             memory                  256Mi   4Gi     -               -               -
Pod                             cpu                     100m    2       -               -               -
Container                       cpu                     100m    2       100m            100m            -
Container                       memory                  32Mi    4Gi     512Mi           512Mi           -
openshift.io/Image              storage                 -       1Gi     -               -               -
openshift.io/ImageStream        openshift.io/image-tags -       20      -               -               -
openshift.io/ImageStream        openshift.io/images     -       10      -               -               -

```
---------

To Provide View access to the User In OCP

```
oc adm policy add-role-to-user view Mack -n NAMESPACE

```

To find out rolebinding assigned for the Project

```
oc get rolebinding -n NAMESPACE

```

To give admin access to project

```
oc get project
oc project projectname
oc adm policy add-role-to-user admin <User> -n <Project>

```


To confirm the access
```
oc describe rolebinding admin
oc describe rolebinding view
```
To Find out the Pod Running in the Node
```
oc adm manage-node NODENAME --list-pods

```

To find out EP of router pod

```
oc get endpoints --namespace=default --selector=router

```
To find out no of router pod in all namespaces

```
oc get route --all-namespaces

```
schedule and unschedule a node

```
oadm manage-node <node1> <node2> --schedulable=false

oadm manage-node <node1> <node2> --schedulable
```

To find out the labels
```
oc get all --show-labels
```

To describe endpoint for particular project

```
oc describe endpoints -n projectname

```
------------
To allow image pulling 

```
oadm policy add-cluster-role-to-group system:image-puller system:authenticated -n NAMESPACE

```
To list project without header

```
oc get project -o name |cut -d '/' -f2

```
To find out running Pod in all namespaces

```
oc get po --all-namespaces |egrep -c Running

```
