Project :deployment of micro-services on GKE.

Tools : Git Hub, Terraform, Kubernets, CloudSDK, Docker, Ingress-Controller and Google Container Registry

GitHub : https://github.com/AtharvaWathodkar/my_exercise_atharva.git

Referances : 

https://registry.terraform.io/providers/hashicorp/google/latest/docs
https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/google_project_service
https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/compute_network
https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/compute_subnetwork
https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/compute_router
https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/compute_router_nat
https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/compute_address
https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/compute_firewall
https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/container_cluster
https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/container_node_pool
https://registry.terraform.io/providers/hashicorp/google/latest/docs/resources/google_service_account
GitLab : https://gitlab.com/atharva_wathodkar/mygooglecloud.git (My Old Lab project)

Example 1 : deployment object to demonstrate cluster autoscaling. used the nginx image and set two replicas to deploy it to the spot instance group that does not have any nodes.

Example 2 : Deployed gcloud service to use workload identity and grant access for the pod to list GS buckets.

Example 3 : deploy the nginx ingress controller using the helm and used reused the deployment object created earlier for the Example 1.

Terraform : Deployed Private VPC, Subnet,Router, Nat, Firewall and GKE (Cluster and node pool) using terraform and kept tfstate file at remote location.
                                                
                                                Create GKE Cluster Using TERRAFORM

Provider.tf : Setup Terraform GCP Provider
                                1. Project ID
                                2. Region
VPC.tf : Setup VPC

Subnet.tf : step is to create a private subnet to place Kubernetes nodes

Router.tf : It will be used with the NAT gateway to allow VMs without public IP addresses to access the internet

Nat.tf :  create Cloud NAT

firewall.tf : This firewall will allow sshing to the compute instances within VPC

Kubernetes.tf : configure the control plane of the cluster itself with native VPC.

Node-pool.tf : Created 2 node pool one without autoscaling and other with autoscaling.

Service_account : created service account to access gcloud storage bucket from CloudSDK container.



