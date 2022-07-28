# Terraform MS Azure Deploy AKS Cluster
[Reference 1](https://docs.microsoft.com/en-us/azure/aks/learn/quick-kubernetes-deploy-portal?tabs=azure-cli)<br/>
[Reference 2](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/container_registry)<br/>
Provision of kubernetes cluster in MS Azure using terraform from on premise system.<br/>
Running Azure Vote app and flask app on kubenetes cluster.<br/>
```
terraform init -upgrade
```
```
terraform plan 
```
```
terraform apply
```
To connect kubernetes cluster in azure
```
az aks get-credentials --resource-group example-resources --name example-aks1
```
To get cluster information
```
kubectl get nodes
``` 
# Deploy azure vote app 
```
kubectl apply -f azure-vote.yaml            
```
To access application (--watch is optional)
```
kubectl get service azure-vote-front [--watch]
``` 
The application is accessible on http://<EXTERNAL-IP><br>
You should see on browser something similar<br/>
<img width="605" alt="Screenshot 2022-07-27 at 15 07 18" src="https://user-images.githubusercontent.com/43514418/181254533-3aa25c2c-59a1-447c-af5f-3dc5d6e23c52.png"><br/>

# Deploy flask web app
```
kubectl apply -f flask-app.yaml            
```
```
kubectl get service flask-app-deployment
```
The application is accessible on http://<EXTERNAL-IP:60000><br>
You should see on browser something similar<br/>
<img width="490" alt="Screenshot 2022-07-28 at 07 52 15" src="https://user-images.githubusercontent.com/43514418/181431046-20e7a7ae-c144-40e0-9f2f-6f3337c77a4a.png">
# Clean up resources
CTRL+C
```
terraform destroy
```
or 
```
az group delete --name example-resources --yes --no-wait
```

