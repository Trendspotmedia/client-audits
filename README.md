# SEO Lead Magnet - Automated Audit System

An automated SEO audit lead generation system that captures leads through a beautiful landing page and delivers comprehensive SEO reports powered by AI.

## 🎯 Overview

This system consists of:
1. **Lead Magnet Landing Page** (`index.html`) - Beautiful form to capture website URL and email
2. **n8n Workflow** (`lead-magnet-seo-audit-workflow.json`) - Automated backend processing
3. **AI-Powered Analysis** - Uses Perplexity, Claude, and Google PageSpeed APIs

## 📁 Files

- `index.html` - Lead magnet landing page (form + design)
- `lead-magnet-seo-audit-workflow.json` - Complete n8n workflow
- `report.json` - Sample report structure

## 🚀 Setup Instructions

### Step 1: Deploy Landing Page

Since GitHub Pages is disabled for this org, deploy `index.html` to one of these platforms:

**Option A: Netlify (Recommended)**
1. Go to [netlify.com](https://netlify.com)
2. Drag and drop `index.html`
3. Get instant free hosting
4. Optional: Add custom domain

**Option B: Vercel**
1. Go to [vercel.com](https://vercel.com)
2. Import this GitHub repository
3. Deploy automatically

**Option C: Cloudflare Pages**
1. Go to [pages.cloudflare.com](https://pages.cloudflare.com)
2. Connect GitHub repo
3. Deploy with free SSL

### Step 2: Import n8n Workflow

1. Sign in to n8n at: `https://tsm-trendspotmedia.app.n8n.cloud`
2. Click **Workflows** → **Import from File**
3. Upload `lead-magnet-seo-audit-workflow.json`
4. The workflow will be imported with all nodes configured

### Step 3: Configure API Credentials

In n8n, add these credentials:

#### 1. Perplexity AI
- **Type**: HTTP Header Auth
- **Header Name**: `Authorization`
- **Header Value**: `Bearer YOUR_PERPLEXITY_API_KEY`
- Get API key: [docs.perplexity.ai](https://docs.perplexity.ai)

#### 2. Google PageSpeed API
- **Type**: Google API
- **API Key**: `YOUR_GOOGLE_API_KEY`
- Enable PageSpeed Insights API in Google Cloud Console
- Get key: [console.cloud.google.com](https://console.cloud.google.com)

#### 3. Claude AI (Anthropic)
- **Type**: HTTP Header Auth  
- **Header Name**: `x-api-key`
- **Header Value**: `YOUR_CLAUDE_API_KEY`
- Get API key: [console.anthropic.com](https://console.anthropic.com)

#### 4. Resend (Email)
- **Type**: HTTP Header Auth
- **Header Name**: `Authorization`  
- **Header Value**: `Bearer YOUR_RESEND_API_KEY`
- Get API key: [resend.com](https://resend.com)
- Configure sender domain: `audit@trendspotmedia.com`

### Step 4: Activate Workflow

1. Open the workflow in n8n
2. Click **Active** toggle (top right)
3. The webhook will be live at: `https://tsm-trendspotmedia.app.n8n.cloud/webhook/seo-audit`

## 🔄 How It Works

```
User fills form (URL + Email)
        ↓
  POST to n8n webhook
        ↓
┌───────────────────────────────┐
│  Perplexity AI Analysis       │ → SEO insights, keywords, competitors
│  +                             │
│  Google PageSpeed             │ → Performance scores
└───────────────────────────────┘
        ↓
  Claude AI formats everything
   into professional HTML email
        ↓
   Resend sends email to lead
        ↓
   Success response to form
```

## 📊 What's Included in the Audit

- **SEO Analysis**: Keyword opportunities, content gaps, competitor insights (Perplexity AI)
- **Performance Scores**: Mobile performance, SEO, accessibility, best practices (PageSpeed)
- **Professional Report**: HTML-formatted email with actionable recommendations (Claude AI)
- **Instant Delivery**: Sent to lead's email within seconds (Resend)

## 🛠️ Troubleshooting

### Webhook not responding?
- Check if workflow is **Active** in n8n
- Verify webhook URL matches landing page: `https://tsm-trendspotmedia.app.n8n.cloud/webhook/seo-audit`
- Test webhook manually with curl or Postman

### API errors?
- Verify all credentials are correctly configured in n8n
- Check API key validity and quotas
- Review n8n execution logs for specific error messages

### Email not sending?
- Verify Resend domain is configured: `audit@trendspotmedia.com`
- Check Resend dashboard for delivery status
- Ensure sender domain has proper DNS records (SPF, DKIM)

## 🎨 Customization

### Update Landing Page
- Edit colors in `index.html` (search for `#667eea`, `#764ba2`)
- Modify benefits/copy in the HTML
- Change form fields if needed

### Modify Workflow
- Adjust AI prompts in n8n nodes
- Add/remove analysis steps
- Change email template in Claude node

## 📝 Notes

- Landing page is mobile-responsive and modern
- Workflow handles errors gracefully
- All API calls are asynchronous for fast response
- CORS is handled properly for cross-origin requests

## 🔐 Security

- Never commit API keys to GitHub
- Use n8n's credential system for all API keys
- Landing page validates input before submission
- All communications over HTTPS

## 📞 Support

For issues or questions:
- Review n8n execution logs
- Check API provider dashboards
- Test each component separately

---

**Created**: December 24, 2025  
**Last Updated**: December 24, 2025  
**Maintained by**: Trendspot Media
