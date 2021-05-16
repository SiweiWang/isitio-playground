
# Getting started

## list istio profile 
`istioctl profile list`

## install istio demo profile
`istioctl manifest apply --set profile=demo`

## enable namespace auto injection
`kubectl label ns default istio-injection=enabled`

## disable namespace auto injection
`kubectl label ns default istio-injection-`

## uninstall istio
`istioctl manifest generate --set profile=demo | kubectl delete --filename -`


# Route incoming traffic

## list virtualservice
`kubectl get virtualservice -n <ns>`

## describe virtualservice
`kubectl describe virtualservice <name> -n <ns>`

## Get ingress ip for aks
```bash
export INGRESS_HOST=$(kubectl \
    --namespace istio-system \
    get service istio-ingressgateway \
    --output jsonpath="{.status.loadBalancer.ingress[0].ip}")
```

# Canary deployment
