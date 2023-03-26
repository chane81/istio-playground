## Install Istio

- istio 기본 설치

  ```bash
  # istio cli 설치
  $ brew install istio

  # istio cli 를 이용한 설치
  $ istioctl install --set profile=demo -y

  ✔ Istio core installed
  ✔ Istiod installed
  ✔ Egress gateways installed
  ✔ Ingress gateways installed
  ✔ Installation complete

  # sidecar proxy auto 설치를 위해 namespace label 설정
  $ kubectl label namespace [namespace 명] istio-injection=enabled
  ```
