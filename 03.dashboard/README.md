## View the Dashboard

- Install Addons

  - grafana, prometheus, kiali, jaeger

  ```bash
  $ kubectl apply -f ../00.istio-bin/istio-1.17.1/samples/addons

  $ kubectl rollout status deployment/kiali -n istio-system
  ```

- Dashboard 지속적확인을 위한 주기적 호출
  ```bash
  $ for i in $(seq 1 100); do curl -s -o /dev/null "http://$GATEWAY_URL/productpage"; done
  ```
