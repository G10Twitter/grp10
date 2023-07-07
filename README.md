#steps to deploy with argoCD using minikube
Activate your minikube by running the command minikube start (that is after you have installed minikube or check the documentation)
Ensure you have pods running on the master node (control plane)
create argocd namespace. Run this 2 commands: kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/core-install.yaml
Creting argocd manifest file form argocd repo: kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/v2.5.8/manifests/install.yaml
verify the items are created with: kubectl get all -n argocd
To access argcd UI, you need port forwaring with this command: kubectl port-forward svc/argocd-server -n argocd 8080:443 
to get your password, you use this command : export argocd_password=$(kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d) echo