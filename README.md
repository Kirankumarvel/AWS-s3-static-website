# 🌐 AWS S3 Static Website Hosting Project

A portfolio-ready static website hosted on **Amazon S3** that demonstrates core cloud fundamentals: **static website hosting**, **secure access controls (IAM + bucket policy)**, and **CORS-aware configuration**. Built with a simple multi-page frontend (Home / About / Contact) and deployed using AWS-native capabilities.

---

## Live Demo

**Website URL:** `https://kk-devops-s3-staticwebsite.s3.eu-west-2.amazonaws.com/index.html`

> ⚠️ **Note:** This is a temporary deployment link for demonstration purposes. The website may be decommissioned after the project showcase period.

---

## 📸 Project Screenshots (add yours later)

Replace the placeholders below with real screenshots (recommended: website pages + S3 settings).

### Homepage
<img width="1887" height="943" alt="image" src="https://github.com/user-attachments/assets/f72029c2-4819-497a-b43e-64251be749f0" />

*Screenshot: Homepage hero section*

### Features Section

<img width="1886" height="955" alt="image" src="https://github.com/user-attachments/assets/e10f5db5-be1c-4578-9dfe-8e99059f5ffd" />

*Screenshot: Features section*

### About Page

<img width="1872" height="965" alt="image" src="https://github.com/user-attachments/assets/14c9be42-1cd1-44fb-98a2-e98e4b47069a" />

*Screenshot: About page*

### Contact Page

<img width="1883" height="967" alt="image" src="https://github.com/user-attachments/assets/e347e06e-1afb-49a7-b268-4c941237b9de" />

*Screenshot: Contact page (form validation/UX)*

### AWS S3 Console Configuration

*Screenshot: S3 static website hosting + permissions configuration*
<img width="1907" height="928" alt="image" src="https://github.com/user-attachments/assets/9ff0c422-15db-4f63-9012-0cdb1d1b8f34" />
<img width="1860" height="665" alt="image" src="https://github.com/user-attachments/assets/a0530237-4def-43e1-b393-a00b3d094fc5" />

> Tip: Create a `docs/screenshots/` folder and drop your images there, then update filenames if needed.

---

## 📋 Project Overview

This project showcases a production-style approach to hosting a static website using **Amazon S3**. It focuses on:
- clean static-site deployment
- secure, controlled public access
- CORS considerations for browser-based apps
- cost-aware design suitable for demo/portfolio workloads

**Site Pages Included**
- `index.html` (Home)
- `about.html` (About)
- `contact.html` (Contact)

---

## 🏗️ Architecture (Current)

```
┌──────────────────────────────┐
│          User Browser         │
└──────────────┬───────────────┘
               │  HTTP
               ▼
┌──────────────────────────────┐
│     Amazon S3 Static Website  │
│  - index.html                 │
│  - about.html                 │
│  - contact.html               │
│  - css/style.css              │
│  - js/script.js               │
│                               │
│  Security / Config:           │
│  - Bucket Policy (public read │
│    for website content)       │
│  - IAM permissions            │
│  - CORS rules (as needed)     │
└──────────────────────────────┘
```

---

## ✨ Features Implemented

### Frontend
- ✅ Responsive layout (HTML/CSS)
- ✅ Multi-page navigation (Home / About / Contact)
- ✅ Styling + animations (CSS)
- ✅ Interactive behavior (JavaScript)

### AWS / Cloud
- ✅ S3 bucket static website hosting enabled
- ✅ Bucket policy for controlled public read access (for website assets)
- ✅ IAM permissions aligned with least-privilege principles (for admin/deploy workflows)
- ✅ CORS-ready configuration for browser scenarios

---

## 🛠️ Tech Stack

| Category | Technologies |
|---------|--------------|
| Frontend | HTML5, CSS3, JavaScript |
| AWS | Amazon S3, IAM |
| Tooling | Git, GitHub, VS Code |

---

## 📁 Repository Structure (matches this repo)

```
AWS-s3-static-website/
├── index.html
├── about.html
├── contact.html
├── css/
│   └── style.css
├── js/
│   └── script.js
└── README.md
```

---

## 🚀 Deployment (High-Level Steps)

### 1) Create an S3 bucket
- Choose a region (this demo uses `eu-west-2`)
- Bucket name must be globally unique (example used here): `kk-devops-s3-staticwebsite`

### 2) Enable Static Website Hosting
Configure:
- **Index document:** `index.html`
- **Error document:** `index.html` or `404.html` (based on your routing preference)

### 3) Configure Permissions (Bucket Policy)
Allow public read access **only** for website files (typical for S3-website endpoint demos).

Example (update bucket name):
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::kk-devops-s3-staticwebsite/*"
    }
  ]
}
```

### 4) Upload the site
Using AWS CLI:
```bash
aws s3 sync . s3://kk-devops-s3-staticwebsite/ --region eu-west-2
```

### 5) Validate
Open:
`https://kk-devops-s3-staticwebsite.s3.eu-west-2.amazonaws.com/index.html`

---

## 🔒 Security Notes (What this demonstrates)

- Least-privilege mindset for IAM permissions
- Bucket policy used to allow only the required access level for static hosting
- No secrets or sensitive data stored in the bucket
- CORS can be tightened to trusted origins depending on your use case

---

## 💰 Cost Awareness

This project is designed to stay within (or close to) AWS Free Tier usage for portfolio workloads:
- minimal storage
- low request volume
- limited bandwidth usage

> Recommendation: set up a billing alarm (e.g., $5) to avoid unexpected charges.

---

## 🔄 Future Enhancements (Roadmap)

- [ ] Add **CloudFront** for HTTPS + edge caching
- [ ] Add a **custom domain** via Route 53 (and ACM certificate for HTTPS)
- [ ] Add **CI/CD** using GitHub Actions (`aws s3 sync` on push)
- [ ] Add backend for contact form using **Lambda + API Gateway**
- [ ] Add monitoring and protection (CloudWatch, WAF) for production-style hardening

---

## 📄 License



---

## 👤 Author

**@Kirankumarvel**
