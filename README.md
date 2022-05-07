# Kubernetes + CI/CD Pipeline Azure DevOps

<b> First of all need to create a Kubernetes Cluster in Microsoft’s Azure Kubernetes Service (AKS) for the project infrastructure. </b>

![kubernetes-resources](https://user-images.githubusercontent.com/85096533/167258834-ee26bc35-2649-4f83-8374-156d447872f5.png)

<b>Once the cluster has been created, the next step is to write the configuration for kubernetes to run the application </b> <br><br>
in the k8s folder you can see three config files:<br>
<b>deployment.yml</b> - the main file, contains the number of replicas and points to other files such as variables public in configmap and secret.<br>
<b>ingress.yml<br>
service.yml<br> </b>

![aks-1](https://user-images.githubusercontent.com/85096533/167258845-b10dca71-6535-4cf0-934d-953fa2265a9d.png)
<hr>

<b>This is how the structure of the entire stages of CI/CD looks like. </b> <br></b>
<b>CI :</b>  <br>
1 - Build a container. <br>
2 - Upload the container to the ACR repository.  <br>
3 - Upload artifacts of config files to the repository.  <br>

<b>CD : </b> <br>
1 - Create a configmap file. which describes our public variables.  <br>
2 - Creating secrets, we create encrypted data configurations.  <br>
    in this project, to pass variables, I used the azure devops library and created a group of variables there.  <br>
3 - Stage of downloading the container and configurations from the repository and launching it in Kubernetes Service Azure.  <br>

<img width="640" alt="k8s-cicd" src="https://user-images.githubusercontent.com/85096533/167259371-7d88b13e-98e0-453c-af9a-0ec2a26cd77f.png">

<hr>

<b>To start working with the project you need: </b> <br>
* Create a kubernetes cluster manually or with the help of terraforms in the cloud

* Download azure cli  [link](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-linux?pivots=apt) 
* Login to azure cloud -<b> az login </b>
* Download kube cli -  [link](https://kubernetes.io/docs/tasks/tools/)  
* Authorize azure kubernetes cluster - <b> az aks get-credentials --name MyManagedCluster --resource-group MyResourceGroup </b>

* After connecting to the cluster, you can install Ingress through the command  <br> <b> kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.2.0/deploy/static/provider/cloud/deploy.yaml </b>

* In Azure devops, need to create pool and agent machine to run CI as well as create an Environment and authorize the kubernetes service cluster
<hr>
<b>Screenshots of variables and kubernetes environment </b>(click to enlarge the image) <br>
[link var](https://user-images.githubusercontent.com/85096533/167261485-b8a20028-1453-47f7-bf21-ad1451c2db1b.jpg) <br>
[link environment](https://user-images.githubusercontent.com/85096533/167261491-6bfa4dce-b064-4a7d-96b8-bf449a2f4b81.jpg) <br>


<hr>
<b> Kubernetes commands: </b> <br>

<b>kubectl get services </b> - view active NODES  <br>
<b>kubectl get pods </b>- view active pods  <br>
<b>kubectl delete all --all  </b>  - clear the cluster completely  <br>
<b>kubectl apply file.yml </b>  - apply configuration file  <br>
<b>kubectl logs pod_name </b> - viewing pod logs  <br>
<b>kubectl get svc -n ingress-nginx --watch  </b> - see IP addresses ingress including public  <br>

<hr>

See also my other projects. [link](https://github.com/asiamegic/)  Good luck! 
