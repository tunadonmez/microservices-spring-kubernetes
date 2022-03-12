# Docker

## Images

--image=tunadonmez/microservices-currency-exchange-service:0.0.12-SNAPSHOT
--image=tunadonmez/microservices-currency-conversion-service:0.0.12-SNAPSHOT

## URLS

#### Currency Exchange Service
- http://localhost:8000/currency-exchange/from/USD/to/TRY

#### Currency Conversion Service
- http://localhost:8100/currency-conversion-feign/from/USD/to/TRY/quantity/10


#### Commands
```

kubectl create deployment currency-exchange --image=tunadonmez/microservices-currency-exchange-service:0.0.12-SNAPSHOT
kubectl expose deployment currency-exchange --type=LoadBalancer --port=8000

kubectl create deployment currency-conversion --image=tunadonmez/microservices-currency-conversion-service:0.0.12-SNAPSHOT
kubectl expose deployment currency-conversion --type=LoadBalancer --port=8100

kubectl get pods --watch

kubectl diff -f deployment.yaml
kubectl apply -f deployment.yaml

kubectl delete all -l app=currency-exchange
kubectl delete all -l app=currency-conversion

kubectl logs -f currency-exchange-8554ddc7b6-779lm
