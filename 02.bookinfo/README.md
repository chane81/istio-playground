## BookInfo 예제

- bookinfo, bookinfo-gateway yaml url

  - bookinfo
    https://raw.githubusercontent.com/istio/istio/release-1.17/samples/bookinfo/platform/kube/bookinfo.yaml
  - bookinfo-gateway
    https://raw.githubusercontent.com/istio/istio/release-1.17/samples/bookinfo/networking/bookinfo-gateway.yaml

- bookinfo service, deployment 배포

  ```bash
  $ kubectl apply -f bookinfo.yaml

  # service, pod 확인
  $ kubectl get svc
  $ kubectl get po
  ```

- bookinfo gateway 배포

  ```bash
  $ kubectl apply -f bookinfo-gateway.yaml
  ```

- 확인

  ```bash
  # istio analyze
  $ istioctl analyze

  ✔ No validation issues found when analyzing namespace: default.

  # minikube tunnel
  minikube tunnel

  $ export INGRESS_HOST=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
  $ export INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="http2")].port}')
  $ export SECURE_INGRESS_PORT=$(kubectl -n istio-system get service istio-ingressgateway -o jsonpath='{.spec.ports[?(@.name=="https")].port}')

  $ echo "$INGRESS_HOST"
  ```

- gateway url get

  ```bash
  $ export GATEWAY_URL=$INGRESS_HOST:$INGRESS_PORT

  $ echo "$GATEWAY_URL"

  # url 확인
  $ echo "http://$GATEWAY_URL/productpage"
  ```
