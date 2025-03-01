# Deployment of a Private Communication in a MultiCloud Environment (AWS and GCP) 100% Automated Using Terraform

<p align="center">
<img src="https://i.imgur.com/M45mwvc.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

## Project Description
This project aimed to establish private, cross-cloud connectivity between Amazon Web Services (AWS) and Google Cloud Platform (GCP). The goal was to set up a secure communication channel that would allow instances on AWS and GCP to communicate with each other over private IPs, eliminating the need for public internet access and enhancing security. By implementing this secure, multi-cloud setup, the project lays the foundation for more advanced architectures and real-world use cases where organizations must bridge resources across different cloud environments for enhanced flexibility, resilience, and operational control.

The solution included provisioning the necessary infrastructure on AWS and GCP using Terraform, configuring network elements such as Virtual Private Clouds (VPCs), firewall rules, and VPN connections to achieve private connectivity. Additionally, network intelligence tools and connectivity tests verified the successful communication between instances across the two cloud platforms.

## Project Objectives
1. **Establish Secure, Private Connectivity**: Enable private, secure communication between AWS EC2 and GCP Compute Engine instances, bypassing the public internet.
2. **Leverage Multi-Cloud Resilience**: Set up a reliable, multi-cloud environment that meets business requirements for high availability and cross-cloud flexibility.
3. **Automate Infrastructure Provisioning**: Use Terraform to automate the provisioning of AWS and GCP resources, ensuring consistency, repeatability, and easier resource management.
4. **Demonstrate Network Testing and Connectivity Verification**: Validate connectivity and performance between AWS and GCP using various network testing tools to ensure an optimal setup.
5. **Document and Review Security Best Practices**: Apply security principles to safeguard data integrity and enforce access controls in the multi-cloud configuration.

## Tools and Technologies
1. **AWS Services**: EC2, VPC, Elastic IP, Key Pair management
2. **Google Cloud Platform (GCP)**: Compute Engine, VPC, VPN, Cloud Shell, Network Intelligence
3. **Terraform**: For infrastructure provisioning and automation on both AWS and GCP
4. **Google Cloud Shell**: Command-line interface for GCP operations and SSH access
5. **AWS CLI and GCP CLI**: For managing cloud resources and configurations
6. **SSH Key Generation**: To create secure keys for access and authentication
7. **Network Intelligence Tools**: To verify connectivity and test network performance across clouds

## Project Solution
### Part 1: Initial Setup and Preparation
1. **Create SSH Keys**: Generated a secure SSH key pair (vm-ssh-key) for access to the virtual machines.
2. **Configure Access on AWS and GCP**: Imported the public key to both AWS and GCP instances to enable secure SSH access.

### Part 2: Infrastructure Provisioning with Terraform
1. **Terraform Preparation**:
   - Set up directories and files in Google Cloud Shell to manage and run Terraform configurations.
   - Created Terraform files:
     - main.tf: Defined the AWS and GCP providers.
     - gcp_variables.tf, aws_variables.tf: Declared necessary variables.
     - gcp_compute.tf, aws_compute.tf: Defined compute instances.
     - gcp_networking.tf, aws_networking.tf: Configured VPC and networking resources.
     - gcp_security.tf, aws_security.tf: Set up firewall and security rules.
     - gcp_outputs.tf, aws_outputs.tf: Configured output variables for post-deployment reference.

2. **Initialize and Deploy Resources**:
   - Ran terraform init to initialize the environment and downloaded necessary plugins.
   - Verified the configuration with terraform validate.
   - Executed terraform plan to review the planned infrastructure deployment.
   - Deployed the resources on AWS and GCP by running terraform apply.

### Part 3: Network Configuration and Connectivity Verification
1. **Set Up Private Communication**:
   - Configured firewall rules on both platforms to allow private IP-based communication.
   - Established VPN tunnels and routing rules to direct traffic between AWS and GCP securely.

2. **Connectivity Testing**:
   - From the GCP Compute Engine instance, initiated an SSH session to test connectivity to the AWS EC2 instance's private IP.
   - Verified network latency and successful communication between instances to confirm cross-cloud connectivity.
   - Used GCP Network Intelligence connectivity tests to visualize traffic paths and verify the reliability of the connection.

## Step By Step Instructions:

### Project Solution Part 1

To successfully execute this project, several prerequisites need to be in place:
1. **Create an AWS Account**: If you haven't done so already, navigate to the AWS platform documentation area, where you can find guidance on setting up an AWS account. Follow the instructions provided to create your account. Once completed, you will have access to the AWS Management Console.
2. **Documentation**: A comprehensive PDF document titled "Hands-on Project Network Solution" will support your implementation. This document contains all necessary commands and files. It is highly recommended that you have this PDF open alongside your working environment to facilitate following along with the implementation steps.

#### Step 1: Create a New Project in Google Cloud Platform (GCP)
1. **Access GCP**: Log into Google Cloud Platform and locate the top section of the interface, which shows "My First Project." Click on it and then select the "New Project" button.
2. **Project Naming**: In the PDF documentation, you will find a Project ID that is recommended for use (e.g., tcb-gcp-aws). Input the Project ID and a unique project name. Ensure you follow the naming conventions (which may require adding numbers or dashes). Once ready, click the "Create" button.

<p align="center">
<img src="https://i.imgur.com/nE3Ks7S.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

3. **Enable Billing**: After project creation, you must enable billing:
   - Click on the newly created project.

<p align="center">
<img src="https://i.imgur.com/v8u89f0.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - From the left menu, select "Billing" to confirm you have a billing account associated with this project.

<p align="center">
<img src="https://i.imgur.com/kFkuhAj.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

4. **Enable Compute Engine API**:
   - Use the link provided in the PDF to enable the Compute Engine API for your project.
   - Follow the prompts to allow API access.

<p align="center">
<img src="https://i.imgur.com/A6j5KWS.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

#### Step 2: Set Up Cloud Shell
1. **Activate Cloud Shell**:
   - Click on the Cloud Shell icon in the top right corner of the Google Cloud Console.
   - The first time you activate it may take a few minutes to provision.

<p align="center">
<img src="https://i.imgur.com/3gXAR7t.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

2. **Download Terraform Files**:
   - Once the Cloud Shell is active, copy the provided command from the documentation to download the Terraform files.

<p align="center">
<img src="https://i.imgur.com/4iBv2Rc.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - After executing the command, use the ls command to confirm that the zip file containing the Terraform files has been downloaded.

<p align="center">
<img src="https://i.imgur.com/GWznXGI.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

3. **Unzip and Organize Files**:
   - Unzip the downloaded file and navigate to the newly created directory using the command cd hands-on-tcb-bmc-gcp/.

<p align="center">
<img src="https://i.imgur.com/t8fF791.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/GNUGQVk.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - Use the ls command to view the files. You'll see several shell script files, including those needed for setting up credentials.

<p align="center">
<img src="https://i.imgur.com/OyeavOe.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

#### Step 3: Configure Script Permissions
1. **Change Permissions**:
   - To execute the shell scripts, modify their permissions using the command chmod +x *.sh.

<p align="center">
<img src="https://i.imgur.com/q2kssjv.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - Confirm that the permissions have been set correctly by running ls -l.

<p align="center">
<img src="https://i.imgur.com/ITKtZz9.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

#### Step 4: Service Account Key Setup
1. **Create a New Service Account Key**:
   - Navigate to the IAM section of GCP, locate the service account created by default, and click on it.

<p align="center">
<img src="https://i.imgur.com/GwHmFrR.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - Go to the "Keys" tab and create a new key, selecting the JSON key type. Download the key to your local machine, keeping track of its location for later upload.

<p align="center">
<img src="https://i.imgur.com/GZEsPpQ.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

2. **Upload the Service Account Key to Cloud Shell**:
   - Use the upload feature in Cloud Shell to upload the JSON key you just downloaded.
   - Verify the upload by running ls in the Cloud Shell to see the JSON file listed.

<p align="center">
<img src="https://i.imgur.com/n9eYXBe.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

3. **Run Credential Setup Script**:
   - Change directories into the hands-on-tcb-gcp-aws folder and execute the gcp_set_credentials.sh script with the path to the uploaded JSON key file as an argument. This will configure Terraform to use the service account credentials for provisioning infrastructure.

<p align="center">
<img src="https://i.imgur.com/kxj8bD5.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/IDlELN9.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

#### Step 5: Set Up AWS Credentials
1. **Access AWS Console**:
   - Log into the AWS Management Console and ensure you are set to the US West (Oregon) region for consistency with the project setup.
2. **Create a New User**:
   - Navigate to the IAM service, click on "Users," and then "Add Users."

<p align="center">
<img src="https://i.imgur.com/wjZZ4QY.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - Create a user named terraform_user, granting only programmatic access (no console access is necessary).

<p align="center">
<img src="https://i.imgur.com/ZZ7yv9B.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

3. **Assign Permissions**:
   - On the permissions page, select "Attach existing policies directly" and grant this user full access for simplicity in this project, allowing Terraform to manage the required services.

<p align="center">
<img src="https://i.imgur.com/KmhKAHx.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/SGcBk5B.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

4. **Create Access Key**:
   - Create Access Key for user "terraform" to access Terraform resources.

<p align="center">
<img src="https://i.imgur.com/eL54oru.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - Download CSV File and rename it to "accessKeys.csv" and move to Desktop folder.

<p align="center">
<img src="https://i.imgur.com/dajWJz2.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

### Project Solution Part 2
In this section, we'll continue with the Terraform implementation to provision the infrastructure on both AWS and Google Cloud Platform (GCP). Here's a quick recap of what we've accomplished so far:

- We have prepared all the necessary files and prerequisites on AWS and GCP to execute the Terraform commands.
- Now it's time to run Terraform and start provisioning the infrastructure.

#### Step-by-Step Directions
1. **Access Cloud Shell**:
   - Return to the Google Cloud Shell.
2. **Navigate to the Project Directory**:
   - Ensure you are in the correct directory by switching to the hands-on folder:

<p align="center">
<img src="https://i.imgur.com/30cidXM.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - Confirm you're in the right folder by listing the files:

<p align="center">
<img src="https://i.imgur.com/O2oOfaR.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

3. **Upload AWS Access Keys to Google Cloud Shell**:
   - Upload the .csv file containing the AWS access keys (e.g., accessKeys.csv) to Google Cloud Shell. This file typically includes both the AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY
   - Confirm that the file has successfully uploaded by listing files in your directory again
   - You should see accessKeys.csv listed among the files.

<p align="center">
<img src="https://i.imgur.com/rEV8bHh.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

4. **Configure AWS Credentials in Google Cloud Shell**:
   - Use the provided script to set up AWS credentials in Google Cloud Shell. Run the following command, substituting the path if needed

```
./aws_set_credentials.sh ~/accessKeys.csv
```

<p align="center">
<img src="https://i.imgur.com/d6obNik.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - This script will configure AWS credentials within the environment, allowing Terraform to interact with AWS services.

5. **Preparing Terraform for Deployment**:
   - Run the script to ensure Terraform is correctly installed and ready to use

```
./get_terraform.sh
```

<p align="center">
<img src="https://i.imgur.com/68FYMao.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - This command will confirm Terraform's setup, allowing you to proceed with initializing and applying your infrastructure configuration.

6. **Set the Google Cloud Project**:
   - Execute the following command to set your active Google Cloud project:

<p align="center">
<img src="https://i.imgur.com/I3PIdNj.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - This ensures that subsequent gcloud commands are run within the context of the specified project. This sets project Id that Terraform will create resources for google cloud.

<p align="center">
<img src="https://i.imgur.com/VmFASWt.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

In this section, we will outline the steps necessary to set up SSH keys, import them into Google Cloud Platform (GCP) and AWS, and execute Terraform commands to provision our infrastructure.

7. **Steps to Set Up SSH Keys**:
   **Generate SSH Keys**
   - To generate a new SSH key pair, use the following command in your Cloud Shell:

   ```
   ssh-keygen -t rsa -f ~/.ssh/vm-ssh-key -C [YOUR-USERNAME]
   ```

<p align="center">
<img src="https://i.imgur.com/5lSYcDv.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - Explanation:
     - -t rsa specifies the type of key to create, which is RSA in this case.
     - -f ~/.ssh/vm-ssh-key sets the file path for the new key.
     - -C [YOUR-USERNAME] adds a comment to the key, usually your username.

8. **Set Permissions for the Private Key**
   - Run the command below to ensure that the private key has the correct permissions:

<p align="center">
<img src="https://i.imgur.com/nWDtGkm.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

   - Explanation: This command restricts the access of the private key file to the owner only, which is essential for security.

9. **Importing the Public Key to GCP**
   **Configure SSH for GCP**
   - From the Cloud Shell, run the following command to import the public SSH key into GCP:

<p align="center">
<img src="https://i.imgur.com/B5E0nXX.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

10. **Verify the Key in GCP**
    - Navigate to the GCP Console and go to the Metadata page of your project.
    - Click on the SSH Keys tab, where you should see your imported SSH key.

<p align="center">
<img src="https://i.imgur.com/ZtG2Wmz.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

11. **Importing the Public Key to AWS**
    **Download the Public Key**
    Download the public key generated in Cloud Shell:
    - File Path: /home/[YOUR-USERNAME]/.ssh/vm-ssh-key.pub

<p align="center">
<img src="https://i.imgur.com/uvSo83a.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/aK4eOfq.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/ripvTb2.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/1hSr30A.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

12. **Import Key Pair into AWS**
    - Go to the AWS Management Console.
    - Navigate to EC2 > Network & Security > Key Pairs.
    - Click on Import Key Pair.

<p align="center">
<img src="https://i.imgur.com/aJlPnAp.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

    - Note: Use the name vm-ssh-key when prompted.
    - Browse and select the file vm-ssh-key.pub.

<p align="center">
<img src="https://i.imgur.com/r6yLOFB.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/WKCDsJT.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

#### Terraform Deployment Steps in Google Cloud Shell
13. **Navigate to the Project Directory**
    - Ensure you are in the hands-on-tcb-bmc-gcp folder:

<p align="center">
<img src="https://i.imgur.com/po9v4ar.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

14. **Change to the Terraform Directory**
    - Go into the Terraform folder:

<p align="center">
<img src="https://i.imgur.com/qW3MTGD.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

15. **Initialize Terraform**
    - Run the command below to initialize Terraform:

<p align="center">
<img src="https://i.imgur.com/bHNpKUL.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

16. **Validate the Terraform Configuration**
    - To ensure that your Terraform configuration is set up correctly, run:

<p align="center">
<img src="https://i.imgur.com/PjKsl1K.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

17. **Check the Terraform Plan**
    - Generate an execution plan to see what resources will be created:

<p align="center">
<img src="https://i.imgur.com/0oaNjaM.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

18. **Start the Terraform Deployment**
    - To start provisioning resources, run the following command and type yes to confirm:

```
terraform apply
```

<p align="center">
<img src="https://i.imgur.com/16DSA9K.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/lH6dQA6.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

19. **Test Connectivity from GCP to AWS Using Private IP**
    - Objective: Confirm that the GCP virtual machine (VM) can reach the AWS EC2 instance using its private IP address.

<p align="center">
<img src="https://i.imgur.com/I2pzgIb.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

    - Click on SSH under the "Connect" column. This will open a new SSH session in a browser window.

<p align="center">
<img src="https://i.imgur.com/qLbtbRA.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

    - If prompted to allow pop-ups, make sure to enable them, then select Connect to start the session.

<p align="center">
<img src="https://i.imgur.com/mBVmKWP.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/epRTEc5.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

20. **Retrieve AWS Private IP**:
    - In the AWS Console, go to EC2 > Instances, locate the instance created with Terraform, and copy its Private IP address.

<p align="center">
<img src="https://i.imgur.com/fpQ3cCG.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/Pcgq2H3.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

21. **Ping the AWS Private IP from GCP VM**:
    - Return to your SSH session on the GCP VM.
    - Run the command:

<p align="center">
<img src="https://i.imgur.com/en7J5Od.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

22. **Run Additional Connectivity Test Using Network Intelligence**
    - Objective: Verify connectivity using Google Cloud's Network Intelligence Center for a more detailed analysis of network paths.

23. **Enable Network Management API**:
    - In the GCP console, go to Network Intelligence > Connectivity Tests.
    - If prompted, enable the Network Management API to proceed.

<p align="center">
<img src="https://i.imgur.com/jlX44va.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

24. **Create a New Connectivity Test**:
    - Click Create Connectivity Test.
    - Name the test (e.g., "gpc-aws-testing").

<p align="center">
<img src="https://i.imgur.com/zB2UngS.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

25. **Define Source and Destination**:
    - Source IP: Set this to the internal IP of your GCP VM. You can retrieve this from the Terraform outputs.

<p align="center">
<img src="https://i.imgur.com/dFBgov1.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

    - Source Network: Select the network used by your GCP VM (e.g., "tcb-gcp-aws").

<p align="center">
<img src="https://i.imgur.com/IKqP8VM.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

    - Destination IP: Paste the Private IP of the AWS EC2 instance.

<p align="center">
<img src="https://i.imgur.com/YJZ5dHo.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

    - Destination Port: Enter 22 (default SSH port).

<p align="center">
<img src="https://i.imgur.com/00fDQDf.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

26. **Run the Test**:
    - Click Create to initiate the test. Once completed, view the results to see if the connectivity is established successfully.

<p align="center">
<img src="https://i.imgur.com/uHBcEPi.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

    - You'll see a detailed diagram of the connectivity path, indicating routing through VPNs, firewalls, and any network hops.

<p align="center">
<img src="https://i.imgur.com/2255szU.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

27. **Outcome**:
    - If the test shows as Reachable, it confirms that the private communication path between the GCP and AWS networks is properly established.

<p align="center">
<img src="https://i.imgur.com/n7nnphL.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/NScYzDa.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

<p align="center">
<img src="https://i.imgur.com/XE0A9hx.png" height="80%" width="80%" alt="Pic"/>
<br />
<br />

I have successfully established seamless, private connectivity between AWS and GCP environments, showcasing a robust, real-world multi-cloud networking solution. This achievement serves as a solid foundation for future cross-cloud integrations, demonstrating advanced technical capabilities and offering a practical framework for organizations that need secure and efficient resource connectivity across multiple cloud providers. This setup is an essential asset for modern enterprises navigating multi-cloud architectures.

## Project Conclusion
The project successfully achieved secure, private connectivity between AWS and GCP environments, providing a scalable solution for cross-cloud networking. This setup exemplifies a viable approach to multi-cloud architectures, allowing organizations to benefit from the strengths of each cloud provider while maintaining secure inter-cloud communication. The infrastructure provisioning and network verification demonstrated the effectiveness of automated deployment using Terraform, as well as the importance of network testing in validating multi-cloud architectures.

### Challenges Encountered
1. **Key Management and Security**: Managing SSH keys across two different platforms posed initial challenges, particularly in key import and secure access configuration.
2. **Firewall and Network Configuration**: Ensuring that firewall rules aligned on both AWS and GCP required careful configuration to allow private IP communication without compromising security.
3. **Cross-Cloud Latency**: Minimal latency was observed, though varying regions or cloud configurations could impact performance.
4. **Terraform Learning Curve**: Fine-tuning the Terraform configuration to work across both cloud platforms required additional learning and testing.

### Lessons Learned
1. **Multi-Cloud Security**: Ensuring proper key management and secure VPN configurations is critical in multi-cloud setups.
2. **Automation Benefits**: Terraform greatly simplifies multi-cloud infrastructure provisioning, though it's essential to validate all configurations before deployment.
3. **Network Testing Importance**: Verifying connectivity with tools like GCP Network Intelligence helped confirm that network paths and permissions were correctly set up.

### Future Improvements
1. **Expand Multi-Region Support**: Extend the setup to include multi-region and multi-zone deployments for improved redundancy and disaster recovery.
2. **Enhanced Automation**: Integrate additional automation to streamline key management and VPN configuration.
3. **Real-Time Monitoring**: Add monitoring tools for real-time health and performance tracking across cloud environments to preemptively address connectivity issues.
4. **Cost Optimization**: Assess and implement cost optimization strategies, such as using reserved instances or savings plans where applicable, to further reduce the cross-cloud communication costs.
