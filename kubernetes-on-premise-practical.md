## Setup Kubernetes Cluster

### Multi Master Nodes
- 꼭 Master Node는 Multi로 구성해라
- 제일 먼저 이것부터 해라
- k8s v1.14.x 이상을 사용하는게 편하다.
  - 1.13.x는 복사 작업들을 해야한다. 귀찮다.

### etcd
- 날려먹으면 상당히 곤란하기에 클러스터 구성 추천
- Master Node 줄일 때 명시적으로 etcd도 빼줘야 한다.

### Proxy Mode
- iptables는 대규모 환경에서 성능 이슈 존재
- ipvs는 성능이 좋지만, 호환성에 대한 테스트 필수


## Cluster Managements

### Management Tool
- Dashboard
  - 뭐 나쁘지 않다.
- kubectl
  - CLI 기본
- VSCode - kubernetes Plugin
  - kubeconfig 파일 이용해 로컬 클러스터 관리 가능
  - YAML 파일 템플릿 제공
  - TreeView를 통해 클러스터 내부 컨테이너 상태 확인 가능

### Namespace 관리 정책
- 권한 부여 등을 고려하면
  - 프로젝트 별로 namespace 할당
  - 조직별로 namespace 할당
- 권한 설정
  - ServiceAccount 생성하고
  - Role 설정하고
  - RoleBinding 하면 namespace 단위로 권한을 줄 수 있다.

## Cluster Enhancement

### MetalLB
- ipvs 사용할 때에는 호환성 확인 필요

### Rook woth Ceph
- Ceph 상당히 안정적인데, 설치/운영하기 어려움
- Rook을 이용해 Ceph 클러스터 생성 및 관리
- 이걸 이용하면 Pod를 특정 노드에 종속시키지 않고 배포 가능
- Ceph 클러스터 구축
  - Bluestore 저장소 설정 : 물리디스크를 직접 Ceph가 관리. 이렇게 하는 것이 성능이 잘 나옴
  - 복제본은 2 또는 3 정도 하면 안정적임


## Monitoring
- blah ablah
  
