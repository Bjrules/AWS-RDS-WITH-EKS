# AWS-RDS-WITH-EKS
Implementation of AWS managed Dadabase RDS with Kubernetes 

### Important things to notes about implementation of Amazon RDS on Kubernetes.
1. Since AWS RDS is a managed Database As A Service, it is thus considered "Production Grade" since it performs better than the traditional installation of MySQL   

## Set Up kubernetes fom Begin.
--- 
- [ ] AWS CLI and Configure
- [ ] Terraform and use the EKS-Terraform Module
- [ ] Install Kubectl
- [ ] Install Ekctl 
- [ ] kubeconfig to connect  `aws eks --region us-east-1 update-kubeconfig --name bnj-cluster`


##### For this particular setup i used Click-Ops to set up RDS see the terraform module to see how to set up RDS in terraform

![alt text](IMG-Screenshots/Screenshot_20260727_225830.png)

![alt text](IMG-Screenshots/Screenshot_20260727_230648.png)

Copy the Endpoint to serve as the ExternalName url address of the database

![alt text](IMG-Screenshots/Screenshot_20260727_231816.png)

Modify it in the manifest .yaml file accordingly.  Note that security is not the subject matter and the is why the secret `rds-mysql-secret` is so open. also be aware that since it is string Data:, we did not  encode the username and password with base64. 

![alt text](IMG-Screenshots/Screenshot_20260728_003013.png)

##### service type `ExternalName` was used to capture the rds Enpoint which was copied form AWS
Note that init container was created that will create the database `bankappdb` which is required for the application to start. init container will start and die after its work is done.
##### Also `admin` was used in palce of `root` because that was what i used when creating the database using ClickOps . 
![alt text](IMG-Screenshots/Screenshot_20260728_003302.png)

![alt text](IMG-Screenshots/Screenshot_20260728_003323.png)

Create all resources using the manifest.yaml

![alt text](IMG-Screenshots/Screenshot_20260727_233536.png)

It worked  , i created acoount and gave myself ₦40,000,000 UD :joy:
![alt text](IMG-Screenshots/Screenshot_20260728_003013.png)

![alt text](IMG-Screenshots/Screenshot_20260728_003458.png)







