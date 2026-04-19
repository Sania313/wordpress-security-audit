# 🔐 WordPress Security Audit — MedShop Pro

> A professional WordPress + WooCommerce security audit simulating a real-world 
> rogue developer attack scenario. 10 vulnerabilities identified including 
> an active malicious backdoor.

---

## 📋 Project Overview

**Client:** MedShop Pro (simulated)  
**Auditor:** Sania  
**Date:** April 2026  
**Stack:** WordPress + WooCommerce + PHP  
**Audit Type:** Full Security & Code Review  

---

## 🎯 Scenario

A healthcare ecommerce store reported a significant drop in sales shortly after 
granting full admin access to an external developer. This audit was conducted 
to identify whether malicious changes were introduced that could be blocking 
legitimate customer purchases.

---

## 🔍 Findings Summary

| # | Finding | Severity |
|---|---------|----------|
| 1 | Unauthorised Administrator Account | 🔴 HIGH |
| 2 | Weak Admin Credentials | 🔴🔴 CRITICAL |
| 3 | Application Passwords Enabled | 🟡 MEDIUM |
| 4 | Code Injection Plugins Installed | 🔴 HIGH |
| 5 | Automatic Updates Disabled | 🟡 MEDIUM |
| 6 | **Malicious Backdoor Code — ACTIVE** | 🔴🔴 CRITICAL |
| 7 | No SSL Certificate Installed | 🔴🔴 CRITICAL |
| 8 | Personal Email for Admin Account | 🟢 LOW |
| 9 | Incorrect Homepage Configuration | 🟢 LOW |
| 10 | RSS Feed Exposing Full Content | 🟢 LOW |

---

## 🚨 Critical Discovery

An active PHP backdoor was found planted in the site's code:

```php
add_action('init', function() {
    if (isset($_GET['dev_bypass'])) {
        define('WOOCOMMERCE_CHECKOUT_BYPASS', true);
        setcookie('admin_preview', '1', time()+3600, '/');
    }
});
```

This code creates a secret checkout bypass triggered by a hidden URL parameter,
directly explaining the reported drop in conversions.

---

## 📁 Repository Structure

wordpress-security-audit/
├── report/
│   └── MedShop-Pro-Security-Audit-Report.pdf
├── evidence/
│   ├── 01-users-list.png
│   ├── 02-suspicious-user.png
│   ├── 03-admin-account.png
│   ├── 04-plugins-list.png
│   ├── 05-suspicious-snippet.png
│   ├── 06-backdoor-code.png
│   ├── 07-no-ssl.png
│   ├── 08-general-settings.png
│   └── 09-reading-settings.png
└── remediation/


---

## 🛠️ Skills Demonstrated

- WordPress security auditing
- Malicious code detection and analysis
- WooCommerce security review
- User access and privilege auditing
- Plugin security assessment
- Professional audit report writing
- Vulnerability severity classification

---

## 📄 Full Report

👉 [Download Full Audit Report (PDF)](report/MedShop-Pro-Security-Audit-Report.pdf)

---

*This project was built as a portfolio piece demonstrating real-world 
WordPress security audit methodology.*



