# Servicee

The test application is Artifactory. Only Kubernetes manifest files introduced with an ingress controller as a loadballander.
It is stored in the **dev** foler.

A self-sign certificate is added.
The command lines are:
```
$ openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -sha256 -days 365
```
The the base64 encoded added to the secrets.yaml
```
$ base64 cert.pem
$ base64 key.pem
```

It is deployed by applying the ArgoCD Kubernetes manifest file after it is commited:
```
$ kubectl apply -f application.yaml --validate=true
```

From this time every new commits will be deployed.

To creacte an externally available endpoint for the loadbalancer you need to run:
```
$ minikube tunnel
```
This should keep running in the background.

*TODO:*

Add ssl to loadbalancer endpont.

To see it from your browser / check results from a console:

```
$ kubectl get svc -n cicd-artifactory-dev
```

You can also read the logs of the application as the output of the logs:

```
$ kubectl get pods -n cicd-artifactory-dev
$ kubectl logs <POD-NAME> -n cicd-artifactory-dev
```
