# Email Setup for Contact Form

## Option 1: Formspree (Recommended - Free & Easy)

### Steps:
1. Go to [formspree.io](https://formspree.io)
2. Sign up with your email
3. Create a new form
4. Set the email to: `founders@quatarly.com`
5. Copy your form ID (looks like: `xpznabcd`)
6. In `contact.html`, replace `YOUR_FORM_ID` with your actual form ID:
   ```html
   <form action="https://formspree.io/f/xpznabcd" method="POST">
   ```

### Features:
- ✅ Free for 50 submissions/month
- ✅ Spam protection
- ✅ Email notifications to founders@quatarly.com
- ✅ No backend code needed

---

## Option 2: EmailJS (Alternative)

### Steps:
1. Go to [emailjs.com](https://www.emailjs.com)
2. Sign up and create a service
3. Connect your GoDaddy email
4. Get your Service ID, Template ID, and Public Key
5. Update contact.html with EmailJS script

---

## Option 3: Resend (Developer-friendly)

### Steps:
1. Go to [resend.com](https://resend.com)
2. Sign up and verify your domain (quatarly.com)
3. Get API key
4. Create a Vercel serverless function to send emails

---

## Current Setup

The contact form is configured for **Formspree**. Just:
1. Sign up at formspree.io
2. Get your form ID
3. Replace `YOUR_FORM_ID` in contact.html
4. Deploy!

Emails will be sent to: **founders@quatarly.com**
