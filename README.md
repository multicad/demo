# Self-healing (Liveness probe)

- Liveness Command probe 설정
~~~
nano exec-liveness.yaml
~~~
![commandProbe01](https://user-images.githubusercontent.com/20763542/106622135-a153a980-65b6-11eb-83da-67ba79da9304.jpg)

-- /tmp/healthy 파일이 존재하는지 확인하는 설정파일
-- 5초마다 해당 파일이 있는지 조회한다.
-- Kubelet이 첫 체크하기 전에 기다리는 시간을 설정한다.

![commandProbe02](https://user-images.githubusercontent.com/20763542/106618921-60a66100-65b3-11eb-8b22-04003d3d86ae.jpg)


- 파일 설정으로 배포
~~~
kubectl create –f exec-liveness.yaml
~~~
![commandProbe03](https://user-images.githubusercontent.com/20763542/106618914-5edc9d80-65b3-11eb-9089-2b2ecc9934ba.jpg)

- 결과 확인
~~~
kubectl describe pod liveness-exec
~~~
![commandProbe04](https://user-images.githubusercontent.com/20763542/106618916-5f753400-65b3-11eb-9d0a-30ccb363e5aa.jpg)

- 파일이 존재하지 않을 경우, 정상 작동에 문제가 있다고 판단되어
kublet에 의해 자동으로 컨테이너가 재시작 된다.
~~~
kubectl get pod liveness-exec -o wide
~~~
![commandProbe05](https://user-images.githubusercontent.com/20763542/106618918-600dca80-65b3-11eb-9868-a71500c4afc6.jpg)
