# EmailJS Setup Instructions

To enable direct email sending from your portfolio contact form, follow these steps:

## 1. Create EmailJS Account

1. Go to [https://www.emailjs.com/](https://www.emailjs.com/)
2. Click "Sign Up" and create a free account
3. Verify your email address

## 2. Add Email Service

1. In the EmailJS dashboard, go to **Email Services**
2. Click **Add New Service**
3. Choose your email provider (Gmail recommended)
4. Follow the instructions to connect your Gmail account
5. Note down your **Service ID** (e.g., `service_abc123`)

## 3. Create Email Template

1. Go to **Email Templates** in the dashboard
2. Click **Create New Template**
3. Use this template content:

**Subject:**
```
New Contact Form Message: {{subject}}
```

**Body:**
```
You have received a new message from your portfolio contact form.

Name: {{from_name}}
Email: {{from_email}}
Subject: {{subject}}

Message:
{{message}}

---
This email was sent from your portfolio contact form.
```

4. Save the template and note down your **Template ID** (e.g., `template_xyz789`)

## 4. Get Your Public Key

1. Go to **Account** → **General**
2. Find your **Public Key** (e.g., `AbCdEfGhIjKlMnOp`)

## 5. Update Your Portfolio

Open `script.js` and replace these placeholders:

```javascript
// Line 198: Replace with your Public Key
emailjs.init("YOUR_PUBLIC_KEY");

// Line 221: Replace with your Service ID and Template ID
emailjs.send('YOUR_SERVICE_ID', 'YOUR_TEMPLATE_ID', templateParams)
```

**Example:**
```javascript
emailjs.init("AbCdEfGhIjKlMnOp");
emailjs.send('service_abc123', 'template_xyz789', templateParams)
```

## 6. Test Your Form

1. Open your portfolio in a browser
2. Fill out the contact form
3. Click "Send Message"
4. You should receive an email at abhijeetkartikeya@gmail.com

## Troubleshooting

- **Free tier limit**: 200 emails/month
- **Check spam folder**: First emails might go to spam
- **Console errors**: Open browser DevTools (F12) to see any errors
- **Email not received**: Verify all IDs are correct in script.js

## Alternative: Use Formspree (Simpler)

If EmailJS seems complicated, you can use Formspree instead:

1. Go to [https://formspree.io/](https://formspree.io/)
2. Sign up for free
3. Create a new form
4. Replace the form in `index.html` with:

```html
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST" class="contact-form">
    <input type="hidden" name="_subject" value="New Portfolio Contact">
    <div class="form-group">
        <label for="name">Name</label>
        <input type="text" name="name" required placeholder="Your Name">
    </div>
    <div class="form-group">
        <label for="email">Email</label>
        <input type="email" name="email" required placeholder="your.email@example.com">
    </div>
    <div class="form-group">
        <label for="subject">Subject</label>
        <input type="text" name="subject" required placeholder="What's this about?">
    </div>
    <div class="form-group">
        <label for="message">Message</label>
        <textarea name="message" rows="5" required placeholder="Your message here..."></textarea>
    </div>
    <button type="submit" class="btn btn-primary">
        <span>Send Message</span>
    </button>
</form>
```

This is simpler but redirects to a thank you page after submission.
