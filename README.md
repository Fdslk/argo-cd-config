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
     ![result](https://user-images.githubusercontent.com/6279298/146896505-bcead6e6-4078-4fd0-ac29-287ec4f0299a.png)
  * how to see argocd UI
    </br>```kubectl get svc -n argocd```
     ![result](https://user-images.githubusercontent.com/6279298/146896613-315f5aae-e7cd-42f7-8ebe-fd5ba90ac587.png)
    </br>```kubectl port-forward -n argocd svc/argocd-server 8080:443```
     ![result](https://user-images.githubusercontent.com/6279298/146896604-014cd48b-fbc2-4f8e-b68c-0ca801ebbdf9.png)
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
    "type": "Opaque"}

  * how to make the argo cd config work
  </br> ```kubectl apply -f application.yaml```
  ![result](https://user-images.githubusercontent.com/6279298/146899503-9dc092c7-d330-493b-aa65-ca0b1de3b1b2.png)
