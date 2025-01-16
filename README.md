# kube-argocd

그리고 미리 MD 파일 작성
MD에 작성할 내용
내가 만든 git 주소를 가지고 Kubernetes 환경에 배포 테스트

Docker Compose로 배포하는것은 1대만 가능하지만
여러대의 서버에 배포를 하게 되면 Kubernetes 가 필요

환경은 우분투 20.04 에 K3S로 진행
개인 컴퓨터로 하는것이라 단일 컴퓨터에 단일 노드
---
# 사전 설치 
설치 방법은 사이트 보면서 그대로 적어두기 
## Helm

## ArgoCD

## Grafana

## Prometheu
---
# pod의 리소스 제한 및 복제
Cpu와 ram 갯수 지정
1대에서 5대까지 증가하는 HPA 설정
이건 프론트엔드와 백엔드하는게 맞고

### ArgoCD 로 배포 후 모니터링

---
# 아쉬운점
DB 부분을 준비하는데 복제를 하게되면 PVC 또는 PV 또는 stateful 및 프록시 연결 해보기
Istio 로 서비 메쉬 해보기
