# namespace-k8s-kubebuilder
kubernetes의 namespace를 watch하여 namespace가 변경 될 경우 deployment를 rollout할 수 있도록 controller를 kubebuilder로 제작


## kubebuilder 
kubebuilder는 Kubernetes Controller 제작  SDK 이다.

## namespace
kubernetes에서 namespace는 논리적으로 리소스를 구분지어 사용할 수 있도록 한다.

## namespace-k8s-controller 동작

1. namespace에 `deploy-inject` Annotation을 확인한다.
2. namespace에 `deploy-inject` 존재 시 deployment에 주입한다.
3. deployment.Annotations과 deployment.Spec.Template.Annotations에 해당 `deploy-inject`를 주입한다.
4. deployment가 rollout 된다. 

## Test
make 명령어를 사용하여 kubernetes 컨테스트의 클러스터에서 실행하고 테스트 할 수 있다.

```
make run
```

## Build
docker를 이용하여 controller를 빌드 할 수 있다.

```
docker build --tag namespace-k8s-controller:0.1 .
```

