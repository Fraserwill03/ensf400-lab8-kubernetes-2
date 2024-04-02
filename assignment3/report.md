you must first start minikube with minikube start

then run $ kubectl apply -f assignment3/ -R which will recursively run kubectl apply -f <file> for all files in assignment3 and its subdirectories

Then to test our nginx service:

```bash
curl http://$(minikube ip)/
```

And to test the app ingress directly:

```bash
curl http://$(minikube ip)/app
```