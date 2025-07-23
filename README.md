# EC2-S3-Project
aws-static-site



---

### 📁 Project Title:

**Static Website Hosting Using AWS S3 and EC2**

---



---

## 📌 Project Overview

This project demonstrates how to **host a static website using AWS S3 and EC2**.
It uses S3 for storing an image (`f1.jpg`) and EC2 (Amazon Linux) to serve a custom HTML file using Apache.

---

## 🔧 Tools & Technologies Used

* AWS S3 (Simple Storage Service)
* AWS EC2 (Amazon Linux 2)
* Apache HTTP Server
* HTML/CSS (Static Website)
* GitHub (Project Documentation)
* PuTTY / Terminal (SSH access)

---

## 🚀 Step-by-Step Implementation

### 1. 🪣 Create an S3 Bucket

* Go to AWS S3 → Create Bucket
* Bucket Name: `mybucketvishwjeetbidkar`
* Uncheck **Block all public access**
* Enable static hosting (optional)

### 2. 🖼️ Upload Image to S3

* Upload `f1.jpg` to the bucket
* Make it **public** by:

  * Adding a bucket policy:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadImage",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::mybucketvishwjeetbidkar/*"
    }
  ]
}
```

* S3 Image URL:
  `https://mybucketvishwjeetbidkar.s3.us-east-1.amazonaws.com/f1.jpg`

---

### 3. 💻 Launch EC2 Instance

* Launch Amazon Linux 2 EC2
* Choose Free Tier (`t2.micro`)
* Open ports: `22` (SSH), `80` (HTTP)
* Create/Select key pair (`.pem`)

---

### 4. 🔑 Connect EC2 Using PuTTY

* Convert `.pem` to `.ppk` using PuTTYgen
* Open PuTTY:

  * Hostname: `ec2-user@<Public IPv4>`
  * Auth: Load `.ppk` file
* Connect to EC2

---

### 5. 🌐 Install Apache Web Server

```bash
sudo yum update -y
sudo yum install httpd -y
sudo systemctl start httpd
sudo systemctl enable httpd
```

---

### 6. ✏️ Create index.html in Apache Root

```bash
cd /var/www/html
sudo nano index.html
```

Paste this HTML:

```html
<!DOCTYPE html>
<html>
<head>
    <title>My Static Website</title>
</head>
<body>
    <h1 style="text-align: center;">Welcome to My Static Website!</h1>
    <div style="text-align: center;">
        <img src="https://mybucketvishwjeetbidkar.s3.us-east-1.amazonaws.com/f1.jpg" alt="F1 Image" width="500">
    </div>
</body>
</html>
```

---

### 7. 🌍 Access Website in Browser

Go to:

```
http://IPv4 Code Copy
```

You should see your hosted webpage with the image from S3.


