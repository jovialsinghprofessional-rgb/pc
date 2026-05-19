# Email Notification System Setup Guide

Your website now has a fully functional contact form that sends email notifications! Follow these steps to activate it.

---

## 🚀 Quick Setup (5 minutes)

### Step 1: Create Free EmailJS Account
1. Go to **[emailjs.com](https://www.emailjs.com/)** and click "Sign Up"
2. Create a free account (no credit card required)
3. Verify your email

### Step 2: Add Email Service
1. In EmailJS dashboard, go to **Email Services** (left sidebar)
2. Click **"Add Service"**
3. Choose **Gmail** (or your preferred email provider)
4. Click **"Create Service"**
5. **Important:** For Gmail, you need an **App Password** (not your regular password):
   - Go to your [Google Account Security](https://myaccount.google.com/security)
   - Enable **2-Factor Authentication** (if not already enabled)
   - Go to **App passwords** → Select Mail & Windows
   - Copy the 16-character password
   - Paste it in EmailJS
6. Click **"Save"**
7. **Copy your Service ID** (you'll need it later)

### Step 3: Create Email Template
1. Go to **Email Templates** in EmailJS dashboard
2. Click **"Create New Template"**
3. Name it: **"contact_form_inquiry"**
4. Use this template:

```
Subject: New Website Inquiry from {{client_name}}

From: {{client_name}}
Email: {{client_email}}
Phone: {{client_phone}}
Service: {{service_type}}
Submitted: {{submitted_at}}

Message:
{{message}}
```

5. Click **"Save"**
6. **Copy your Template ID**

### Step 4: Create Confirmation Email (for clients)
1. Click **"Create New Template"** again
2. Name it: **"client_confirmation"**
3. Use this template:

```
Subject: We received your inquiry! 📧

Hi {{client_name}},

Thank you for reaching out to PixelCraft Studio! We've received your inquiry and will get back to you within 24 hours.

Best regards,
PixelCraft Team
```

5. Click **"Save"**
6. **Copy this Template ID too**

### Step 5: Get Your Public Key
1. Go to **Account** (top right menu)
2. Under **API Keys**, copy your **Public Key**

### Step 6: Update Your Website Code
1. Open your `index.html` file
2. Find this line (around line 1075):
```javascript
emailjs.init("YOUR_EMAILJS_PUBLIC_KEY_HERE");
```
Replace with your actual public key:
```javascript
emailjs.init("abc123xyz_YOUR_ACTUAL_PUBLIC_KEY_def456");
```

3. Find this section (around line 1100):
```javascript
await emailjs.send(
  "YOUR_EMAIL_SERVICE_ID",
  "YOUR_EMAIL_TEMPLATE_ID",
```
Replace with:
```javascript
await emailjs.send(
  "service_abc123xyz",  // Your Service ID from Step 2
  "template_contact_inquiry",  // Your Template ID from Step 3
```

4. Find the email address to receive notifications (around line 1120):
```javascript
to_email: "jovialsinghprofessional@gmail.com",
```
Replace with **your email address**

5. Find the confirmation email template part (around line 1130):
```javascript
await emailjs.send(
  "YOUR_EMAIL_SERVICE_ID",
  "YOUR_CONFIRMATION_TEMPLATE_ID",
```
Replace with:
```javascript
await emailjs.send(
  "service_abc123xyz",  // Same Service ID
  "template_client_confirmation",  // Your confirmation template ID from Step 4
```

---

## ✅ Testing Your Setup

1. Save your changes
2. Go to your website
3. Scroll to the **Contact** section
4. Fill out the form:
   - **Name:** John Doe
   - **Email:** your-email@gmail.com
   - **Phone:** 98765 43210
   - **Service:** Business Website
   - **Message:** Test message

5. Click **"Send Inquiry"**
6. You should see: ✓ "Inquiry sent successfully!"
7. Check your inbox for:
   - **Email 1:** Admin notification with all details
   - **Email 2:** Confirmation to the client

---

## 📧 What You'll Receive

### Admin Email (To You):
```
Subject: New Website Inquiry from John Doe

From: John Doe
Email: john@example.com
Phone: 98765 43210
Service: Business Website
Submitted: 5/19/2026, 3:45 PM

Message:
Test message
```

### Client Email (To Them):
```
Subject: We received your inquiry! 📧

Hi John Doe,

Thank you for reaching out to PixelCraft Studio! We've received your inquiry and will get back to you within 24 hours.

Best regards,
PixelCraft Team
```

---

## 🔧 Configuration Details

| Item | Where to Find | Purpose |
|------|--------------|---------|
| **Public Key** | EmailJS Account → API Keys | Initializes EmailJS |
| **Service ID** | Email Services → Your Gmail | Connects to email provider |
| **Template ID** | Email Templates → Template name | Email format & content |
| **To Email** | Your email address | Where inquiries are sent |

---

## 🛡️ Security Notes

✅ **Safe & Secure:**
- Your actual email password is NOT in the code
- All data is encrypted in transit
- EmailJS handles email delivery securely
- Public Key is safe to expose (keys work together for security)

---

## 🚨 Troubleshooting

### "Error sending inquiry"
- ❌ Check if Public Key is correct
- ❌ Check if Service ID is correct
- ❌ Check if Template IDs are correct
- ❌ Check your Gmail App Password (not regular password)
- ✅ Open browser console (F12) to see error details

### Emails not arriving
- ❌ Check spam/promotions folder
- ❌ Verify recipient email is correct
- ❌ Gmail App Password might be incorrect
- ✅ Check EmailJS dashboard for failed attempts

### Form not submitting
- ❌ Check all required fields are filled
- ❌ Check email format is valid
- ❌ Open browser console (F12) for JavaScript errors

---

## 📱 What Happens When Someone Submits

```
Customer fills form
        ↓
JavaScript captures data
        ↓
Validates form fields
        ↓
Sends to EmailJS
        ↓
EmailJS processes with template
        ↓
Sends email to you ✉️
        ↓
Sends confirmation to customer ✉️
        ↓
Shows success message on page
        ↓
Clears form for next inquiry
```

---

## 💰 Pricing

**EmailJS Free Tier:**
- ✅ 200 emails/month
- ✅ Unlimited accounts
- ✅ All features
- ✅ Perfect for most websites

**Paid Plans:**
- Start at $9.99/month for 1,000 emails
- Perfect if you get lots of inquiries

---

## 📝 Email Template Variables

You can customize email templates using these variables:
- `{{client_name}}` - Customer's name
- `{{client_email}}` - Customer's email
- `{{client_phone}}` - Customer's phone
- `{{service_type}}` - Selected service
- `{{message}}` - Inquiry message
- `{{submitted_at}}` - Submission date/time

---

## 🎉 Done!

Your website now has a fully functional email notification system. Every inquiry will:
- ✅ Come to your inbox
- ✅ Show customer confirmation
- ✅ Display success message
- ✅ Have professional formatting

**Questions?** Check EmailJS docs at [emailjs.com/docs](https://www.emailjs.com/docs/)

---

## 🔄 Quick Reference Card

```
📧 EmailJS Account: www.emailjs.com
🔑 Public Key Location: Account → API Keys
📧 Email Service: Email Services section
📋 Templates: Email Templates section
🔗 Website Code: index.html (search for YOUR_EMAILJS_PUBLIC_KEY_HERE)
```

---

**Created:** May 19, 2026  
**Status:** ✅ Ready to Use
