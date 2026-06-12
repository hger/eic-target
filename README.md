kubectl get lease -n kube-system cp-kube-vip-lease -o jsonpath='{.spec.holderIdentity}'

kubectl get pods -n kube-system -l app.kubernetes.io/name=kube-vip --field-selector spec.nodeName=<TARGET-NODE-NAME>

kubectl delete pod <KUBE-VIP-POD-NAME> -n kube-system
