This assignment demonstrates the deployment of a MERN Stack Blog Application using **Terraform** and **Ansible** on **AWS** infrastructure.



## **Goal**
To automate the provisioning and deployment of a blog application:
- Frontend hosted on S3 (Static Website)
- Backend running on EC2 (Ubuntu 22.04), managed by PM2
- MongoDB Atlas as the database
- Media uploads to S3 via IAM credentials



## **Tools & Services Used**
- **Terraform** – Infrastructure provisioning (EC2, S3, IAM, Security Groups)
- **Ansible** – Backend provisioning, environment setup, and application launch
- **AWS EC2** – Running the Node.js backend server
- **AWS S3** – 
  - Frontend: static website hosting
  - Media: image uploads via backend
- **MongoDB Atlas** – Cloud database
- **PM2** – Process manager for the backend
- **Ubuntu 22.04** – EC2 instance OS



## **Deployment Steps Summary**

### 1. Infrastructure Setup (Terraform)
- Created VPC resources, security group, EC2 instance, IAM user & policies
- Created S3 buckets for frontend hosting and media uploads
- Configured Terraform outputs to pass credentials to Ansible

### 2. Backend Provisioning (Ansible)
- Used Ansible playbook with role-based structure:
  - Cloned the blog app repository
  - Created a `.env` file using secrets and MongoDB/S3 info
  - Installed Node.js using NVM
  - Installed dependencies and started backend with PM2

### 3. Frontend Deployment
- Created `.env` for frontend with API URL and media base URL
- Built the frontend using `pnpm`
- Uploaded static files to S3 frontend bucket



## **Screenshots**
You can find in the `/screenshots` folder.



## **Issues Faced**
- **EC2 instance IAM Role conflict** – resolved by using access key for media upload only
- **PM2 not persisting after reboot** – fixed by adding PM2 startup to Ansible role
- **CORS issues in S3 media bucket** – solved by applying correct CORS policy via Terraform




## **Author**
Asail – Infrastructure Engneering Bootcamp | Week 11
