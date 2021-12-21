# how to set up argo-cd-config

* defination
  * argo cd is a common CD tool for kubernates

* steps
  * create a namespace in local k8s cluster by follow cmd:
    </br> ``` kubectl create namespace argocd ```
  * pull necessary resource to namespace
    </br>``` kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml ```
  * check argo cd resource
    </br>``` kubectl get pods -n argocd ```
     ![result](/images/argocdpods.png)
  * how to see argocd UI
    </br>```kubectl get svc -n argocd```
     ![result](/images/getargocdsvc.png)
    </br>```kubectl port-forward -n argocd svc/argocd-server 8080:443```
     ![result](/images/argocdUI.png)
  * how to login argo ci ui
    </br>```kubectl get secret argocd-initial-admin-secret -n argocd  -o yaml```
    ```{
    "apiVersion": "v1",
    "data": {
        "password": "QXp0TnVWZWVra1NSa3Jxdw=="
    },
    "kind": "Secret",
    "metadata": {
        "creationTimestamp": "2021-12-20T14:17:16Z",
        "managedFields": [
            {
                "apiVersion": "v1",
                "fieldsType": "FieldsV1",
                "fieldsV1": {
                    "f:data": {
                        ".": {},
                        "f:password": {}
                    },
                    "f:type": {}
                },
                "manager": "argocd-server",
                "operation": "Update",
                "time": "2021-12-20T14:17:16Z"
            }
        ],
        "name": "argocd-initial-admin-secret",
        "namespace": "argocd",
        "resourceVersion": "3856",
        "selfLink": "/api/v1/namespaces/argocd/secrets/argocd-initial-admin-secret",
        "uid": "0d60128c-7140-429e-89e9-6fe59ae9e86d"
    },
    "type": "Opaque"}```