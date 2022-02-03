## HPA

```bash
$ alias kubectl='kubectl -n game-2048'

$ kubectl autoscale deployment depl-2048 --cpu-percent=50 --min=1 --max=20
horizontalpodautoscaler.autoscaling/depl-2048 autoscaled

$ kubectl get hpa
NAME        REFERENCE              TARGETS         MINPODS   MAXPODS   REPLICAS   AGE
depl-2048   Deployment/depl-2048   <unknown>/50%   1         20        2          18s

$ kubectl run -i --tty load-generator --rm --image=busybox --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://serv-2048; done" &

$ kubectl get hpa depl-2048 --watch

$ kubectl get deployment depl-2048

```
