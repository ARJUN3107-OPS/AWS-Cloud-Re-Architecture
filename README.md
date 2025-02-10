# VPROFILE - AWS Cloud Re-Architecture

## Objective
The goal of this project was to re-architect the existing VPROFILE multi-tier web application stack on AWS to:
- Build a flexible and scalable infrastructure.
- Eliminate upfront costs by leveraging AWS services.
- Implement Infrastructure as Code (IaC), Platform as a Service (PaaS), and Software as a Service (SaaS).
- Optimize for agility, scalability, and business continuity.

## Scenario
The existing setup comprised services running on a mix of Physical, Virtual, and Cloud machines. Challenges included:
- High operational overhead.
- Limited scalability.
- Uptime and performance concerns.
- Manual management of infrastructure and deployments.

## AWS Services Used
- **Elastic Beanstalk** - Application hosting and management.
- **EC2** - Virtual Machines for the Tomcat Application Server.
- **NGINX/ELB** - Load Balancing.
- **Auto Scaling** - Automated VM scaling.
- **S3/EFS** - Storage solutions.
- **RDS (MySQL)** - Managed Relational Database.
- **Elastic Cache (Memcached)** - In-memory caching.
- **Active MQ** - Message brokering.
- **Route 53** - DNS management.
- **CloudFront** - Content Delivery Network (CDN).

## Step-by-Step Execution
### 1. Initial Setup
- Logged into AWS account.
- Created key pairs for secure SSH access.
- Configured security groups for Elastic Cache, RDS, and Active MQ.

### 2. Database Initialization
- Launched an EC2 instance.
- Initialized and configured the RDS MySQL database.

### 3. Elastic Beanstalk Configuration
- Created an Elastic Beanstalk environment.
- Updated security groups to allow internal traffic between backend services.

### 4. Load Balancer and Health Checks
- Configured the ELB to check `/login` for health status.
- Added an HTTPS listener on port 443.

### 5. Build and Deploy Application Artifact
- Built the application with backend configurations.
- Deployed the artifact to Elastic Beanstalk.

### 6. CDN and DNS Configuration
- Created a CloudFront distribution with an SSL certificate.
- Updated GoDaddy DNS zones to point to the CloudFront URL.

### 7. Testing and Validation
- Verified the application’s functionality via the configured URL.

## Architecture Overview
### Existing vs AWS Setup
| Component      | Existing Setup        | AWS Setup          |
|--------------|---------------------|-------------------|
| Load Balancer | NGINX | ELB in Beanstalk |
| Scaling | Manual | Auto Scaling |
| Storage | NFS | EFS/S3 |
| Database | MySQL on VM/EC2 | RDS |
| Caching | Memcached on VM/EC2 | Elastic Cache |
| Messaging | RabbitMQ on VM/EC2 | Active MQ |
| DNS | GoDaddy/Local DNS | Route 53 |
| CDN | None | CloudFront |

## Things Learned
- **Automation:** Used AWS Elastic Beanstalk for seamless deployment and management.
- **Scalability:** Implemented Auto Scaling to dynamically adjust resources based on demand.
- **High Availability:** Leveraged ELB and RDS Multi-AZ deployment for failover protection.
- **Cost Optimization:** Eliminated CapEx and optimized OpEx through managed AWS services.
- **Security Best Practices:** Configured security groups and IAM roles for access control.

## Conclusion
This project successfully re-architected the VPROFILE application on AWS, resulting in:
- Reduced operational overhead with managed services.
- Improved scalability and performance.
- Automated deployments and monitoring.
- Enhanced security and reliability with AWS best practices.

This project is an example of how cloud-native architectures can transform traditional setups into efficient, automated, and cost-effective solutions. 🚀

