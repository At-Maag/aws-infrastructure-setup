# 🚀 Deploy a Static Website on AWS with S3 + CloudFront + Custom Domain

This guide walks you through hosting a secure static website using:
- **Amazon S3** – for static site storage
- **CloudFront** – for HTTPS + CDN
- **Route 53** – for custom domain DNS
- **AWS Certificate Manager (ACM)** – for a free SSL certificate

---

## ✅ Prerequisites

- AWS account
- Domain name (via Route 53 or transferred)
- Static website (e.g., `index.html`)

---

## 🧭 Recommended Setup Order

1. Create S3 bucket and upload site
2. Enable website hosting on S3
3. Request an ACM certificate
4. Set up CloudFront
5. Point domain in Route 53
6. Test and troubleshoot

---

## 🪣 Step 1: Create an S3 Bucket

- Name it the same as your domain (e.g., `exampledomain.com`)
- Uncheck **Block all public access**
- Enable **Static website hosting**
  - Index document: `index.html`

📁 Upload your site files (e.g., `index.html`, `style.css`)

---

## 🔐 Step 2: Request an SSL Certificate via ACM

1. Go to **AWS Certificate Manager**
2. Click **Request a certificate**
3. Choose **Public certificate**
4. Add:
   - `exampledomain.com`
   - `www.exampledomain.com`
5. Use **DNS validation**
6. Copy the **CNAME record values**

> ⚠️ **Important:** Copy only the **value**, such as `abc123.acm-validations.aws`, **not** prefixes like `https\072\057\057`.

7. Add these CNAMEs to **Route 53 > Hosted zone**.

⏱️ Wait ~10–30 minutes for ACM to validate.

---

## 🌐 Step 3: Create a CloudFront Distribution

- Origin domain: use S3 **website endpoint**, e.g., `exampledomain.com.s3-website-us-west-2.amazonaws.com`
- Viewer protocol policy: **Redirect HTTP to HTTPS**
- Alternate domain names (CNAMEs):
  - `exampledomain.com`
  - `www.exampledomain.com`
- SSL Certificate: choose the validated ACM cert
- Default root object: `index.html`
- Enable HTTP/2 and HTTP/3

---

## 🌍 Step 4: Point Your Domain (Route 53)

Create two **A records**:

### Root Domain (`exampledomain.com`)
- Type: A – Alias
- Alias to: CloudFront distribution

### Subdomain (`www.exampledomain.com`)
- Same as above

---

## 🧪 Step 5: Test

Go to:
- `https://exampledomain.com`
- `https://www.exampledomain.com`

You should see your website live and secured with HTTPS.

---

## 🛠️ Troubleshooting

| Issue | Fix |
|-------|-----|
| `403 Forbidden` | Use **S3 website endpoint**, not bucket URL |
| Certificate stuck at `Pending Validation` | Check DNS CNAME records in Route 53 |
| `NXDOMAIN` or domain not found | Confirm alias records are correct |
| SSL/Cipher error | You may have copied incorrect CNAME values. Only use values like `abc123.acm-validations.aws` without slashes |

---

## 📁 Optional Project Structure

```
aws-static-site/
├── index.html
├── assets/
│   └── styles.css
├── README.md
└── deploy-manual.md
```

---

> Created for anyone looking to host a secure static site on AWS.

---
