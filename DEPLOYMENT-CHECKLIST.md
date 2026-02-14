# Railway Template Deployment Checklist

This document outlines the steps to publish this template to Railway's template marketplace.

## ✅ Completed

- [x] Created GitHub repository: https://github.com/matthewspear/railway-booklore
- [x] Complete README.md with features and setup instructions
- [x] Railway template configuration (template.json)
- [x] Docker Compose file for local testing
- [x] Environment variable documentation (.env.example)
- [x] Setup guide (SETUP.md)
- [x] Contributing guidelines (CONTRIBUTING.md)
- [x] Proper licensing (MIT for template, AGPLv3 for BookLore)
- [x] .gitignore for sensitive files

## 🔨 Next Steps

### 1. Test the Template Locally

```bash
cd ~/Developer/railway-booklore
cp .env.example .env
# Edit .env with your values
docker compose up -d
# Visit http://localhost:6060
```

### 2. Create Railway Template

1. **Log in to Railway Dashboard**
   - Visit https://railway.app/dashboard
   - Sign in with GitHub account (matthewspear)

2. **Create New Template**
   - Click "Templates" in sidebar
   - Click "Create Template" or "New Template"
   - Select "From GitHub Repository"
   - Choose `matthewspear/railway-booklore`

3. **Configure Template**
   - **Name:** BookLore
   - **Description:** Self-hosted digital library with smart shelves, auto metadata, device sync, and built-in reader
   - **Icon:** Upload BookLore logo or use URL: https://raw.githubusercontent.com/booklore-app/booklore/develop/assets/logo%20with%20text.svg
   - **Category:** Database / Self-Hosted / Productivity
   - **Source:** GitHub repository (matthewspear/railway-booklore)

4. **Template Configuration**
   - Railway should auto-detect `template.json`
   - Verify services are configured:
     - ✅ BookLore (web service)
     - ✅ MariaDB (database service)
   - Verify volumes are mapped:
     - ✅ booklore-data → /app/data
     - ✅ booklore-books → /books
     - ✅ booklore-bookdrop → /bookdrop
     - ✅ mariadb-data → /config

5. **Set Referral Code**
   - In template settings, ensure referral code is: `matthewspear`
   - This enables 50% revenue share on deployments

6. **Publish Template**
   - Click "Publish Template"
   - Template will be reviewed by Railway team
   - May take 1-3 business days for approval

### 3. Update README with Correct Deploy URL

After Railway approves the template, update the deploy button URL in README.md:

**Current (placeholder):**
```markdown
[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/template/booklore?referralCode=matthewspear)
```

**Update to actual template URL:**
```markdown
[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/template/[ACTUAL-TEMPLATE-SLUG]?referralCode=matthewspear)
```

Railway will provide the actual template slug after approval.

### 4. Test Deployment

1. **Click the Deploy Button**
   - Use the Railway deploy button from your README
   - Deploy to a test project

2. **Verify Everything Works**
   - [ ] BookLore service starts successfully
   - [ ] MariaDB service starts successfully
   - [ ] Database connection is established
   - [ ] Web interface is accessible
   - [ ] Can create admin account
   - [ ] Can upload and import books
   - [ ] Volumes persist after restart
   - [ ] Environment variables are substituted correctly

3. **Test Edge Cases**
   - [ ] Custom domain configuration
   - [ ] OIDC authentication setup
   - [ ] SMTP email configuration
   - [ ] Database backup and restore
   - [ ] Service restart/redeploy

### 5. Promote the Template

Once approved and tested:

1. **Share on Social Media**
   - Twitter/X: Tag @Railway, @BookLore_app
   - Reddit: r/selfhosted, r/BookCollecting
   - Hacker News: Show HN post

2. **Update BookLore Community**
   - Post in BookLore Discord: https://discord.gg/Ee5hd458Uz
   - Create GitHub discussion in BookLore repo
   - Submit to awesome-selfhosted lists

3. **Create Blog Post/Tutorial**
   - Write a quick "Deploy BookLore in 60 seconds" guide
   - Include screenshots
   - Share deployment experience

4. **Monitor and Iterate**
   - Watch for GitHub issues
   - Monitor Railway template analytics
   - Update template based on user feedback
   - Keep BookLore version updated

## 📊 Revenue Expectations

With Railway's 50% referral kickback:

- **Starter Plan:** $5/month → $2.50 commission
- **Developer Plan:** $10/month → $5.00 commission
- **Team Plan:** $20/month → $10.00 commission

**Example projections:**
- 10 deployments/month (avg $10/month) = $50/month passive income
- 50 deployments/month = $250/month passive income
- 100 deployments/month = $500/month passive income

## 🔗 Useful Links

- **Railway Templates Docs:** https://docs.railway.app/reference/templates
- **Railway Template Marketplace:** https://railway.app/templates
- **BookLore Repo:** https://github.com/booklore-app/booklore
- **BookLore Docs:** https://booklore.org/docs/getting-started
- **BookLore Discord:** https://discord.gg/Ee5hd458Uz

## ⚠️ Important Notes

1. **Template JSON Validation**
   - Ensure `template.json` follows Railway's schema
   - Test locally before publishing
   - Railway may reject templates with syntax errors

2. **Image Availability**
   - Verify `booklore/booklore:latest` is always available
   - Monitor BookLore releases for breaking changes
   - Consider pinning to specific version tags for stability

3. **Database Compatibility**
   - LinuxServer MariaDB image may change
   - Test new image versions before updating template
   - Provide migration path if changing database image

4. **Volume Persistence**
   - Railway volumes are persistent by default
   - Warn users about volume deletion consequences
   - Recommend regular backups

5. **Cost Transparency**
   - Railway charges for:
     - Compute time (per service)
     - Volume storage (per GB)
     - Network egress (per GB)
   - Typical BookLore deployment: $10-20/month
   - Heavy usage (many books, users): $20-50/month

## 🎯 Success Metrics

Track these to measure template success:

- **Deployments:** Total number of installs from template
- **Active Deployments:** Currently running instances
- **GitHub Stars:** Community interest indicator
- **Issues/PRs:** Community engagement
- **Revenue:** Monthly referral earnings
- **User Feedback:** Discord mentions, tweets, reviews

## 🚀 Next Actions (Priority Order)

1. ✅ **Test locally** with docker-compose
2. ⏳ **Create Railway template** via dashboard
3. ⏳ **Submit for approval** (wait 1-3 days)
4. ⏳ **Update README** with actual deploy URL
5. ⏳ **Test deployment** end-to-end
6. ⏳ **Promote template** on social media
7. ⏳ **Monitor and iterate** based on feedback

---

**Created:** 2026-02-15
**Status:** Ready for Railway template creation
**Repository:** https://github.com/matthewspear/railway-booklore
