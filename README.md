# mic-test

## Notes
1. Ensure you have the RH registration variables filled in:
```
export MINISHIFT_USERNAME='<RED_HAT_USERNAME>'
export MINISHIFT_PASSWORD='<RED_HAT_PASSWORD>'
```


## Start minishift
```
minishift delete & minishift start
```

## Login to OpenShift and create a new project
```
oc login -u ocuser
oc new-project mic-test
```

## Deploying

1. Deploy AMQ Messaging Broker
```
oc process -f amq-template.yaml -p AMQ_USER=mquser -p AMQ_PASSWORD=password | oc create -f -
```
2. Deploy Gateway
```
oc process -f gateway-template.yaml | oc create -f -
```
3. Deploy IBS Demo Wrapper
```
oc process -f ibs-wrapper-template.yaml | oc create -f -
```
4. Deploy TSYS Demo Wrapper
```
oc process -f tsys-wrapper-template.yaml | oc create -f -
```
5. Deploy BN Demo Wrapper
```
oc process -f bn-wrapper-template.yaml | oc create -f -
```