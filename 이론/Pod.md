# Pod

## 실행 순서

1. `Scheduler`는 API서버를 감시하면서 할당되지 않은unassigned `Pod`이 있는지 체크
2. `Scheduler`는 할당되지 않은 `Pod`을 감지하고 적절한 `노드`node에 할당 (minikube는 단일 노드)
3. 노드에 설치된 `kubelet`은 자신의 노드에 할당된 `Pod`이 있는지 체크
4. `kubelet`은 `Scheduler`에 의해 자신에게 할당된 `Pod`의 정보를 확인하고 컨테이너 생성
5. `kubelet`은 자신에게 할당된 `Pod`의 상태를 `API 서버`에 전달



## 컨테이너 상태 모니터링

* 쿠버네티스는 컨테이너가 생성되고 서비스가 준비되었다는 것을 체크하는 옵션을 제공하여 초기화하는 동안 서비스되는 것을 막을 수 있음

* livenessProbe
  * 컨테이너가 정상적으로 동작하는지 체크
  * 정상적으로 동작하지 않으면 컨테이너 재시작
  * http get 요청으로 확인
* readinessProbe
  * 컨테이너가 준비되었는지 체크
  * 정상적으로 준비되지 않았다면 **Pod으로 들어오는 요청을 제외**
  * livenessProbe와 차이점은 문제가 있어도 Pod을 재시작하지 않고 요청만 제외