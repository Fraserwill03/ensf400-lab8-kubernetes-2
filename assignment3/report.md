you must first start minikube with minikube start

then run $ kubectl apply -f assignment3/ -R which will recursively run kubectl apply -f <file> for all files in assignment3 and its subdirectories