# demo

Liveness Command probe 설정
~~~
nano exec-liveness.yaml
~~~


/tmp/healthy 파일이 존재하는지 확인하는 설정파일
5초마다 해당 파일이 있는지 조회한다.
Kubelet이 첫 체크하기 전에 기다리는 시간을 설정한다.


파일이 존재하지 않을 경우, 정상 작동에 문제가 있다고 판단되어
kublet에 의해 자동으로 컨테이너가 재시작 된다.

파일 설정으로 배포
~~~
kubectl create –f exec-liveness.yaml
~~~
Describe에서의 설정내용
~~~
kubectl describe pod liveness-exec
~~~
