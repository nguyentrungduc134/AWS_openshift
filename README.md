
# OKD Installation on AWS 

This guide provides step-by-step instructions for installing OKD on AWS using a User-Provisioned Infrastructure (UPI). The process follows the official OKD 4.17 documentation.

---

## **1. Preparation**

### **a. Architecture Diagram**
Include a clear architecture diagram to visualize the AWS infrastructure required for OKD installation. The diagram should illustrate:

- VPC with public and private subnets.
- Load Balancers for control-plane and compute nodes.
- Instances for the bootstrap, control-plane (master), and worker nodes.
- Associated security groups, IAM roles, and DNS configurations.

---

### **b. Requirements**
Refer to the official OKD documentation for installation requirements:
- Minimum hardware requirements.
- AWS service limits and configurations.
- Network prerequisites, including subnet, VPC, and load balancer setup.

[OKD 4.17 UPI AWS Installation Requirements](https://docs.okd.io/4.17/installing/installing_aws/upi/upi-aws-installation-reqs.html)

---

### **c. Prerequisites**
Ensure the following prerequisites are fulfilled before proceeding:

1. **Install Required Tools**  
   Follow these guides to install the necessary tools:

   - **OpenShift CLI (`oc`)**:  
     [Installing oc CLI](https://docs.okd.io/4.17/cli_reference/openshift_cli/getting-started-cli.html)  

   - **kubectl**:  
     [Install kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)  

   - **Terraform**:  
     [Terraform Installation Guide](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli)  

   - **AWS CLI**:  
     [Install AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

2. **AWS Credentials**  
   Configure AWS CLI with credentials having sufficient permissions to create and manage AWS resources.  
   ```bash
   aws configure
   ```

3. **DNS Configuration**  
   Set up your domain to point to AWS load balancers for the API and applications. Update records in your external DNS provider as needed.

4. **Prepare Ignition Configuration**  
   - Generate manifests and ignition files using the `openshift-install` binary.
   - Modify configurations if customizations are required for your setup.

Detailed Steps:  
[Preparing to Install on AWS UPI](https://docs.okd.io/4.17/installing/installing_aws/upi/upi-aws-preparing-to-install.html)

---

Let me know if you'd like sections for deployment, troubleshooting, or automating tasks!
