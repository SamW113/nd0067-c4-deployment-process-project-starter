# Infrastructure Description

## Overview

This document outlines the infrastructure setup for the Udagram application, which includes an API, a frontend application, and a PostgreSQL database hosted on AWS. The infrastructure leverages various AWS services to ensure scalability, reliability, and performance.

## Components

1. **Amazon RDS (Relational Database Service)**

   - **Purpose**: Hosts the PostgreSQL database for the application.
   - **Configuration**:
     - Instance Type: db.t2.micro
     - Storage: 20 GB
     - Multi-AZ: No
     - Backup: Automated backups enabled
     - Endpoint: `mypostgres-database-1.c5szli4s4qq9.us-east-1.rds.amazonaws.com`
     - Master Username: `admin`
     - Database Name: `udagram`

2. **Amazon S3 (Simple Storage Service)**

   - **Purpose**: Stores static assets such as images and frontend build artifacts.
   - **Configuration**:
     - Bucket Name: `myprojectmcbucket`
     - CORS Configuration: Allows cross-origin requests from the frontend application.

3. **AWS Elastic Beanstalk**

   - **Purpose**: Hosts the backend API and manages the deployment process.
   - **Configuration**:
     - Environment Name: `udagram-api-dev`
     - Instance Type: t2.medium
     - Platform: Node.js 14
     - Key Pair: `mykeypair`

4. **Frontend Application**
   - **Purpose**: The user interface for the Udagram application.
   - **Hosting**: Deployed on S3 and served through CloudFront for better performance.

## Architecture Diagram

![Architecture Diagram](path/to/your/architecture-diagram.png)

## Details

- **Amazon RDS**: The PostgreSQL database is configured to handle user data and application data. It is accessible from the Elastic Beanstalk environment.
- **Amazon S3**: The S3 bucket is used to store images uploaded by users and the frontend build files. CORS is configured to allow requests from the frontend application.
- **Elastic Beanstalk**: The backend API is deployed on Elastic Beanstalk, which automatically handles scaling and load balancing. The EB CLI is used for deployment and management.
