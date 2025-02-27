# AWS Architecture: Storage & Connectivity

## Where Website Files Will Be Stored
- Website files (**HTML, CSS, JavaScript**) are stored in an **Amazon S3 bucket**.
- Delivered via **Amazon CloudFront (CDN)** for faster global access.

## Where Product Images Will Be Stored
- **Product images (75GB)** are stored in **Amazon S3 (Standard Storage)** for **scalability** and **high availability**.
- Cached and delivered via **Amazon CloudFront** to enhance page load speed.

## How They Connect
1. **Users Access the Website**  
   - Requests go through **Amazon CloudFront**, which caches static files (website and images).

2. **Dynamic Requests Go to EC2**  
   - CloudFront routes requests requiring **dynamic processing** (e.g., login, orders, database queries) to **EC2 instances behind a Load Balancer**.

3. **Auto Scaling Ensures Performance**  
   - **Auto Scaling** dynamically adds or removes **EC2 instances** based on website traffic.

4. **Database & Customer Uploads**  
   - Customer data (**orders, user profiles**) is stored in **Amazon RDS (MySQL)**.  
   - **User uploads** are stored in **Amazon S3**.

5. **Backups & Long-Term Storage**  
   - **Daily backups** are sent to **Amazon S3 Glacier** for cost-efficient long-term storage.
