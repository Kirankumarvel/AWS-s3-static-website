# AWS S3 Static Website — Cloud Infrastructure Project

This project demonstrates how to host a production-style static website on AWS using **Amazon S3**, **CloudFront**, **Route 53**, **IAM**, and a **CORS-aware configuration**. It’s designed to be portfolio-ready and focused on secure static hosting, CDN delivery, custom-domain routing, and cost-conscious operations aligned with AWS best practices.

---

## Tech Stack

- **Amazon S3** (static website hosting / object storage)
- **AWS CloudFront** (CDN, HTTPS, edge caching)
- **Amazon Route 53** (DNS + alias routing)
- **AWS IAM** (least-privilege access)
- **CORS** (cross-origin configuration for browser-based apps)

---

## Portfolio Summary

Deployed an enterprise-style static website on **Amazon S3** with **IAM least-privilege access**, **CORS configuration**, and **CloudFront CDN delivery**. Implemented a **custom-domain DNS flow with Route 53**, static website hosting, secure permissions, and a cost-aware architecture guided by **AWS Well-Architected** principles.

---

## Why This Project Matters

- Demonstrates practical cloud fundamentals using fully managed AWS services.
- Shows how static websites can be **fast, scalable, reliable, and inexpensive**.
- Highlights recruiter-relevant AWS topics: **IAM**, **bucket policies**, **CDN (CloudFront)**, **DNS (Route 53)**, and secure web delivery.

---

## Architecture

**Primary request flow:**

`User → Route 53 → CloudFront → S3 Bucket`

**Optional redirect flow (recommended for custom domains):**

`www.<domain> (S3 redirect bucket) → redirect → <domain> (root)`

---

## Features

- Static website hosting from **Amazon S3**
- **CloudFront** in front of S3 for **HTTPS** and edge caching
- **Route 53 alias records** for custom-domain routing
- **IAM least-privilege** access for deployment and administration
- **Bucket policy** for controlled public access (only where required)
- **CORS configuration** for frontend asset/API scenarios
- Custom **index** and **error** documents
- Cost-aware setup suitable for portfolio/demo workloads

---

## AWS Concepts Demonstrated

### 1) Amazon S3 static website hosting
- Upload `index.html` (and optionally `404.html`)
- Enable **Static website hosting** on the bucket
- Configure:
  - Index document (e.g., `index.html`)
  - Error document (e.g., `404.html`)

### 2) CloudFront for HTTPS + performance
S3 **website endpoints do not support HTTPS directly**, so CloudFront is used to:
- Serve the site over HTTPS
- Cache content at edge locations for lower latency
- Improve global performance and user experience

### 3) Route 53 for custom domains (DNS)
Route 53 provides DNS routing using:
- **A / AAAA alias records** pointing your domain to CloudFront
- Optional `www` routing strategy (redirect or alternate record)

### 4) IAM least-privilege access
Access is scoped to the minimum required actions for:
- Uploading website assets
- Managing cache invalidations (optional)
- Limiting administrative permissions to reduce risk

### 5) Bucket policy design (controlled public access)
Depending on the setup:
- Public access may be allowed only for the **specific objects** intended for web hosting, or
- Access may be restricted so CloudFront is the only approved reader (recommended in production-style setups)

### 6) CORS configuration (browser compatibility)
CORS is included for situations where the frontend:
- Loads assets cross-origin, or
- Calls APIs and requires browser-approved cross-origin behavior

---

## Getting Started (High-Level)

1. Build or collect your static site files:
   - `index.html`
   - `404.html` (optional)
   - CSS/JS/assets

2. Create and configure an S3 bucket:
   - Enable static website hosting
   - Set index/error documents
   - Apply the appropriate public access + bucket policy strategy

3. Create a CloudFront distribution:
   - Set origin to your S3 (website endpoint or S3 origin depending on your design)
   - Enable HTTPS
   - Configure caching behaviors
   - (Optional) Add custom domain + ACM certificate

4. Configure Route 53:
   - Create hosted zone (if needed)
   - Add alias record(s) to CloudFront
   - Add `www` redirect strategy if desired

5. Validate:
   - Site loads via CloudFront domain
   - Site loads via custom domain
   - Error routing behaves as expected
   - CORS headers behave as intended for your use case

---

## Notes on Cost Awareness

This setup is designed to be budget-friendly for demos and portfolios:
- S3 storage costs scale with content size
- CloudFront costs scale with bandwidth/requests
- Route 53 hosted zone + queries are typically low-cost for small sites

---

## License

Add a license if you plan to make this repository public (e.g., MIT).

---
