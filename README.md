# Terraform MS Azure Deploy AKS Cluster
[Reference 1](https://docs.microsoft.com/en-us/azure/aks/learn/quick-kubernetes-deploy-portal?tabs=azure-cli)<br/>
[Reference 2](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs/resources/container_registry)

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
To deploy azure vote app 
```
kubectl apply -f azure-vote.yaml            
```
To access application 
```
kubectl get service azure-vote-front --watch
``` 
The application is accessible on http://EXTERNAL-IP<br>
You should see on browser something similar<br/>
<img width="693" alt="Screenshot 2022-07-27 at 15 06 15" src="https://user-images.githubusercontent.com/43514418/181254368-0d61a89e-a46f-4a06-b78e-1fe8f8964b0c.png">

# Clean up resources
CTRL+C
```
terraform destroy
```
or 
```
az group delete --name example-resources --yes --no-wait
```

