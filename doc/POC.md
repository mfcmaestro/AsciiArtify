## ArgoCD access

1. Expose the the service via port-forward by running the command: 
`kubectl port-forward -n demo svc/ambassador 8088:80`

2. Open ArgoCD UI following the link https://localhost:8080 (Accept the risks)

3. To sign in to the UI use the default username `admin`. To get the Password from k8s secret run the following command:
`kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo`

4. Here is the small demo on how to navigate in ArgoCD.
![argocd_demo](../blob/gifs/ArgoCD.gif)