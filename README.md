# gke-network-policy


Make the demo files executable:
```
cd gke-network-policy
chmod -R 755 *
```
First, set the Google Cloud region and zone.

Set the Google Cloud region.
```
gcloud config set compute/region "us-west1"
```

Set the Google Cloud zone.
```
gcloud config set compute/zone "us-west1-c"
```

Google Cloud Service APIs, and have been enabled for you:
```
# Output
compute.googleapis.com
container.googleapis.com
cloudbuild.googleapis.com
```

In addition, the Terraform configuration takes three parameters to determine where the Kubernetes Engine cluster should be created:

project ID
region
zone
For simplicity, these parameters are specified in a file named terraform.tfvars, in the terraform directory.

To ensure the appropriate APIs are enabled and to generate the terraform/terraform.tfvars file based on your gcloud defaults, run:
```
make setup-project
```
Type y when asked to confirm.

This will enable the necessary Service APIs, and it will also generate a terraform/terraform.tfvars file with the following keys.

Verify the values themselves will match the output of gcloud config list by running:
cat terraform/terraform.tfvars
Copied!
Provisioning the Kubernetes Engine cluster
Next, apply the Terraform configuration within the project root:
make tf-apply
Copied!
When prompted, review the generated plan and enter yes to deploy the environment.
This will take several minutes to deploy.

Task 2. Validation
Terraform outputs a message when the cluster's been successfully created.

...snip...
google_container_cluster.primary: Still creating... (3m0s elapsed)
google_container_cluster.primary: Still creating... (3m10s elapsed)
google_container_cluster.primary: Still creating... (3m20s elapsed)
google_container_cluster.primary: Still creating... (3m30s elapsed)
google_container_cluster.primary: Creation complete after 3m34s (ID: gke-demo-cluster)

Apply complete! Resources: 5 added, 0 changed, 0 destroyed.
Test completed task

Click Check my progress to verify your performed task. If you have successfully deployed necessary infrastructure with Terraform, you will see an assessment score.