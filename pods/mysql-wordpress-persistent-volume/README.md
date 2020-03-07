# start wordpress

## k is alias of kubectl

    $ k apply -f mysql-pv.yaml
    $ k apply -f wordpress-pv.yaml
    $ k apply -k ./
    $ k get pv
    $ k get pvc

# get http response from load balancer of wordpress

    $ k get services wordpress
    > NAME        TYPE           CLUSTER-IP      EXTERNAL-IP   PORT(S)        AGE
    > wordpress   LoadBalancer   10.97.160.240   <pending>     80:31873/TCP   16m

    $ curl -L 10.97.160.240

# remove wordpress

    $ k delete -k ./

