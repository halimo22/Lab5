## Steps : 

- 1- Create docker image 
docker build /NginxDockerImage -t nginx-custom 
docker image has script to generate ssl certificates and nginx config to support 443,80 . 
Check them out. " Useful in docker project "
- 2- docker tag nginx-custom nginx-custom:local
tag to use minikube to import the image to its images 
- 3- minikube image load nginx-custom:local    " If we are using regular kuberenets, this step isnt needed we can just build the image "
now, image is added to minikube 
- 4- apply the service and deployment files
imagePullpolicy must be set to never because 1- default value is always 2- makes it check online and return with an error that it didnt find the image
- 5- get the pods ip addresses 
kubectl get pods -o wide
- 5- access any of the deployment pods by using 
kubectl get pods 
kubectl exec -it <pod-name> -- sh     --> this command opens another nginx server as a command-line terminal, we created 3 so we can use 1 of them to test
- 6-  use 
curl -k http://pod-ip

and 
curl -k https://pod-ip 

** dont use pod ip of the pod u are using to test. **
- 7 - should return the nginx welcome page . screenshot and done . 

