# BookLore Railway Template - Setup Guide

This guide covers deployment, configuration, and common use cases for running BookLore on Railway.

## 🚀 Quick Deploy

1. **Click the Deploy Button**
   - Visit the [README](./README.md) and click "Deploy on Railway"
   - Sign in to Railway (or create an account)
   - Confirm the template deployment

2. **Wait for Deployment**
   - Railway will provision both BookLore and MariaDB services
   - Initial deployment takes ~2-3 minutes
   - Watch the build logs in the Railway dashboard

3. **Access Your Instance**
   - Railway generates a public URL automatically
   - Click the URL in your project dashboard
   - Create your admin account on first visit

## 🔧 Configuration

### Environment Variables

All required environment variables are pre-configured by the template. You can customize:

| Variable | Purpose | When to Change |
|----------|---------|----------------|
| `TZ` | Timezone | Match your local timezone |
| `USER_ID` / `GROUP_ID` | File permissions | If using network storage |
| `DISK_TYPE` | Storage type | Set to `NETWORK` for NFS/SMB |

### Custom Domain

1. Go to **Project Settings** → **Domains**
2. Click **Add Domain**
3. Enter your custom domain (e.g., `books.example.com`)
4. Update your DNS records:
   - **Type:** CNAME
   - **Name:** `books` (or your subdomain)
   - **Value:** The Railway-provided domain

### HTTPS/SSL

Railway provides automatic HTTPS for all deployments:
- ✅ Auto-provisioned SSL certificates
- ✅ Force HTTPS redirect
- ✅ HTTP/2 support

## 📚 Adding Books

### Via Web Upload

1. Log in to your BookLore instance
2. Click **Add Books** in the sidebar
3. Select files (EPUB, PDF, CBZ, CBR)
4. Wait for metadata enrichment
5. Review and confirm import

### Via BookDrop (Planned)

**Note:** Railway doesn't currently support direct volume access from your local machine. BookDrop works within the container but requires API integration for external uploads.

Future options:
- REST API upload endpoint
- S3/Cloudflare R2 integration
- WebDAV access

## 👥 User Management

### Creating Users

1. Log in as admin
2. Go to **Settings** → **Users**
3. Click **Add User**
4. Enter username, email, password
5. Assign role (Admin, User, Guest)

### OIDC Authentication

Enable single sign-on with Google, GitHub, or other OIDC providers:

1. Get OIDC credentials from your provider
2. Add environment variables to your BookLore service:
   ```
   OIDC_ENABLED=true
   OIDC_PROVIDER_URL=https://accounts.google.com
   OIDC_CLIENT_ID=your-client-id
   OIDC_CLIENT_SECRET=your-client-secret
   ```
3. Restart the service
4. Users can now sign in with OIDC

## 📧 Email Configuration

### Send Books to Kindle

1. Configure SMTP in Railway:
   ```
   SMTP_HOST=smtp.gmail.com
   SMTP_PORT=587
   SMTP_USER=your-email@gmail.com
   SMTP_PASSWORD=your-app-password
   SMTP_FROM=booklore@example.com
   ```
2. Add your Kindle email to your user profile
3. Whitelist the sender email in Amazon's "Personal Document Settings"
4. Click the "Send to Kindle" button on any book

### Supported Providers

- Gmail (use App Passwords)
- SendGrid
- Mailgun
- AWS SES
- Any standard SMTP server

## 🗄️ Database Management

### Backups

Railway provides automatic backups for volumes. Manual backup options:

1. **Via Railway CLI:**
   ```bash
   railway run mysqldump -u booklore -p booklore > backup.sql
   ```

2. **Via Dashboard:**
   - Navigate to MariaDB service
   - Click **Volumes** → **Download**

### Restore from Backup

```bash
railway run mysql -u booklore -p booklore < backup.sql
```

## 📊 Monitoring

### Health Checks

BookLore includes a built-in health endpoint:
- **URL:** `/api/v1/healthcheck`
- **Interval:** 60 seconds
- **Timeout:** 10 seconds

### Logs

View real-time logs in Railway:
1. Go to your project dashboard
2. Click the **BookLore** service
3. Open the **Logs** tab
4. Filter by level (info, warn, error)

### Metrics

Railway provides automatic metrics:
- CPU usage
- Memory usage
- Network traffic
- Request volume

## 🔒 Security

### Best Practices

1. **Use Strong Passwords**
   - Railway auto-generates secure database passwords
   - Use a password manager for admin accounts

2. **Enable HTTPS**
   - Always use the Railway-provided HTTPS URL
   - Never force HTTP-only access

3. **Regular Updates**
   - Update the BookLore image periodically
   - Railway supports automatic deployments on image updates

4. **Backup Regularly**
   - Schedule regular database exports
   - Download volumes to local storage

### Access Control

- Use OIDC for enterprise deployments
- Enable two-factor authentication (via OIDC provider)
- Review user permissions regularly
- Disable guest access in production

## 🐛 Troubleshooting

### BookLore Won't Start

1. Check the deployment logs in Railway
2. Verify database connection:
   - Ensure MariaDB service is healthy
   - Check `DATABASE_URL` format
3. Restart both services (MariaDB first, then BookLore)

### Database Connection Errors

```
Error: Unable to connect to database
```

**Solution:**
1. Verify MariaDB is running (check service status)
2. Confirm environment variables are set correctly
3. Check Railway's private networking is enabled
4. Restart the BookLore service

### Books Not Appearing

1. **Check volume mounts:**
   - Verify `/books` volume is attached
   - Check permissions (USER_ID/GROUP_ID)

2. **Metadata issues:**
   - Wait for background enrichment to complete
   - Check logs for API rate limits (Google Books, Open Library)

3. **Cache problems:**
   - Clear browser cache
   - Restart BookLore service

### Upload Failures

```
Error: File upload failed
```

**Solution:**
1. Check file size limits (Railway default: 500MB per request)
2. Verify supported formats (EPUB, PDF, CBZ, CBR)
3. Check volume storage space (Railway dashboard)
4. Try smaller batches (upload 10-20 books at a time)

## 🔄 Updates & Maintenance

### Updating BookLore

Railway doesn't auto-update Docker images. To update:

1. **Via Template Redeploy:**
   - Delete current BookLore service (keep MariaDB)
   - Re-add using the template
   - Volumes persist automatically

2. **Via Image Tag Change:**
   - Edit `template.json` to use a specific version
   - Redeploy via Railway dashboard

3. **Manual Update:**
   - Fork this repository
   - Update `template.json` with desired image tag
   - Deploy from your fork

### Database Migrations

BookLore handles migrations automatically on startup. When updating:

1. Backup your database first
2. Deploy the new version
3. Check logs for migration status
4. Verify data integrity

## 📞 Support

- **BookLore Issues:** [GitHub Issues](https://github.com/booklore-app/booklore/issues)
- **Railway Issues:** [Railway Docs](https://docs.railway.app/)
- **Template Issues:** [This Repository Issues](#)
- **Community:** [BookLore Discord](https://discord.gg/Ee5hd458Uz)

## 📚 Resources

- [BookLore Documentation](https://booklore.org/docs/getting-started)
- [Railway Documentation](https://docs.railway.app/)
- [BookLore GitHub](https://github.com/booklore-app/booklore)
- [Railway Templates Guide](https://docs.railway.app/reference/templates)
