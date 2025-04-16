# Secret

* 쿠버네티스는 `ConfigMap`과 유사하지만, 보안 정보를 관리하기 위해 `Secret`을 별도로 제공
* ConfigMap과 차이점은 데이터가 `base64`로 저장된다는 점 말고는 거의 없음 
* Secret은 보안 정보를 다루기 때문에 당연히 암호화될 거라고 생각할 수 있지만, 실제로는 그대로 저장
  * etcd에 접근이 가능하다면 누구나 저장된 Secret을 확인할 수 있음
  * 따라서 vault (opens new window)와 같은 외부 솔루션을 이용하여 보안을 강화

