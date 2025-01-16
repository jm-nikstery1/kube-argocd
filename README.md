# kube-argocd

- 게시판 프로젝트를 https://github.com/jm-nikstery1/final-board-docker
Kubernetes 환경에 배포 테스트


- Docker Compose로 배포하는것은 1대만 가능하지만
여러대의 서버에 배포를 하게 되면 Kubernetes 가 필요


- 환경은 우분투 20.04 에 K3S로 진행,
개인 컴퓨터로 하는것이라 단일 컴퓨터에 단일 노드
---
# 사전 설치 

## Helm
- curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
- chmod 700 get_helm.sh
- ./get_helm.sh

## ArgoCD
- kubectl create namespace argocd
- kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

## Kubernetes Metrics Server
- kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml

## Prometheus
- kubectl create namespace monitoring 
- helm install prometheus prometheus-community/kube-prometheus-stack --namespace monitoring

## Grafana
- kubectl create namespace monitoring
- helm install grafana grafana/grafana --namespace monitoring

## Nginx Ingress Controller 
- kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/main/deploy/static/provider/cloud/deploy.yaml
 

---
# 리소스 제한 및 HPA 설정
Cpu 사용량 과 Ram 용량 리소스 제한 지정
최소 1게 pod 에서 최대 5대 pod 까지 증가하는 HPA 설정

HPA(Horizontal Pod Autoscaling)
## ArgoCD 로 배포 후 모니터링

---
# 아쉬운점
- 도메인 필요 - 개인 컴퓨터 1대로 하면서 nginx ingress controller 부분에서 제한 조건이 생김 
- DB 부분을 준비 - 복제를 하게되면 PVC 또는 PV 또는 stateful 및 프록시 연결 해보기
- Istio 로 서비 메쉬 해보기
