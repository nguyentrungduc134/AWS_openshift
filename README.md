
# OKD Installation on AWS 

This guide provides step-by-step instructions for installing OKD on AWS . The process follows the official OKD 4.17 documentation.

---

## **1. Preparation**

### **a. Architecture Diagram**
![image](https://github.com/user-attachments/assets/fc97f2ec-c767-4f62-9a0c-7e83455da7d9)


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

---

For OKD installation on AWS, a domain is required for accessing the cluster. You can use **Amazon Route 53** to create a public hosted zone for DNS management. Here's how to handle this setup:

1. **Public Hosted Zone without Domain Registration**  
   - Create a public hosted zone in Route 53 for the desired domain name (e.g., `mydomain.com`), even if the domain is not yet registered.  
   - The hosted zone allows you to create DNS records that point to AWS resources (such as load balancers for the OKD API and ingress router).  
   - When ready, you can later transfer the domain to another DNS provider and update its nameservers to match those provided by Route 53.

2. **Setup API and App DNS Records**  
   - Add DNS `A` or `CNAME` records for the API server and application router.
   - Example records:
     - `api.mydomain.com` → Points to the load balancer for the API server.
     - `*.apps.mydomain.com` → Points to the load balancer for ingress router.

3. **Route 53 Pricing**  
   - **Hosted Zone Cost**: $0.50 per hosted zone per month.  
   - **Query Cost**: $0.40 per million queries for the first billion queries.  
     Pricing details: [Route 53 Pricing](https://aws.amazon.com/route53/pricing/)

4. **Switching to Another DNS Provider**  
   - When migrating the domain to another provider, update the domain's nameservers to point to the new provider.
   - Export DNS records from Route 53 and import them into the new DNS service for a seamless transition.

---

Would you like me to include detailed steps for creating a hosted zone or adding specific DNS records in Route 53?

---

Would you like me to include detailed steps for creating a hosted zone or adding specific DNS records in Route 53?

4. **Prepare Ignition Configuration**  
   - Generate manifests and ignition files using the `openshift-install` binary.
   - Modify configurations if customizations are required for your setup.

Detailed Steps:  
[Preparing to Install on AWS UPI](https://docs.okd.io/4.17/installing/installing_aws/upi/upi-aws-preparing-to-install.html)

---

Let me know if you'd like sections for deployment, troubleshooting, or automating tasks!
