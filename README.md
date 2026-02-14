# BookLore on Railway

[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/template/booklore?referralCode=matthewspear)

**BookLore** is a self-hosted, multi-user digital library that brings your entire book collection under one roof. Organize, read, annotate, sync across devices, and share—all without relying on third-party services.

## ✨ Features

- 📚 **Smart Shelves** – Custom and dynamic shelves with rule-based Magic Shelves, filters, and full-text search
- 🔍 **Automatic Metadata** – Covers, descriptions, reviews, and ratings from Google Books, Open Library, and Amazon
- 📖 **Built-in Reader** – Open PDFs, EPUBs, and comics in-browser with annotations and highlights
- 🔄 **Device Sync** – Connect Kobo, use OPDS-compatible apps, or sync with KOReader
- 👥 **Multi-User Ready** – Individual shelves, progress, and preferences per user
- 📥 **BookDrop** – Drop files into a watched folder for automatic import
- 📧 **One-Click Sharing** – Send books to Kindle, email, or friends instantly

## 🚀 Deploy to Railway

Click the button above to deploy BookLore to Railway. The template includes:

- **BookLore** – The main application (port 6060)
- **MariaDB** – Database for storing library metadata
- **Persistent Volumes** – For books, application data, and BookDrop

## 📋 Configuration

### Environment Variables

The following environment variables are automatically configured by the template:

#### Application Settings

| Variable | Description | Default |
|----------|-------------|---------|
| `USER_ID` | User ID for file permissions | `1000` |
| `GROUP_ID` | Group ID for file permissions | `1000` |
| `TZ` | Timezone for the application | `Etc/UTC` |

#### Database Connection

| Variable | Description | Generated |
|----------|-------------|-----------|
| `DATABASE_URL` | MariaDB connection URL | ✅ Auto |
| `DATABASE_USERNAME` | Database username | ✅ Auto |
| `DATABASE_PASSWORD` | Database password | ✅ Auto |

#### Storage Configuration

| Variable | Description | Default |
|----------|-------------|---------|
| `DISK_TYPE` | Storage type (`LOCAL` or `NETWORK`) | `LOCAL` |

### Volumes

The template creates three persistent volumes:

- **`/app/data`** – Application data (settings, user preferences)
- **`/books`** – Your book library storage
- **`/bookdrop`** – Drop folder for automatic import

## 📖 Getting Started

1. Click the "Deploy on Railway" button
2. Configure your Railway project (select a name, confirm settings)
3. Wait for deployment to complete (~2-3 minutes)
4. Click the generated URL (Railway will provide a public URL)
5. Create your admin account on first visit
6. Start building your library!

## 📥 Using BookDrop

BookDrop automatically imports books from a watched folder:

1. Upload files to the `/bookdrop` volume
2. BookLore detects and parses them automatically
3. Metadata is fetched from Google Books and Open Library
4. Review and import from the BookLore web interface

**Note:** Railway doesn't currently support direct volume access. You can upload books through the web interface or use the REST API to manage your library.

## 🔧 Advanced Configuration

### Custom Domain

1. Go to your Railway project settings
2. Navigate to the BookLore service
3. Add a custom domain under "Settings > Networking"
4. Update your DNS records as instructed

### OIDC Authentication

BookLore supports OIDC providers (Google, GitHub, etc.). See the [official documentation](https://booklore.org/docs/getting-started) for setup instructions.

Add these environment variables to your BookLore service:

```
OIDC_ENABLED=true
OIDC_PROVIDER_URL=https://your-provider.com
OIDC_CLIENT_ID=your-client-id
OIDC_CLIENT_SECRET=your-client-secret
```

### Email Configuration (for Kindle delivery)

To send books to Kindle or via email:

```
SMTP_HOST=smtp.example.com
SMTP_PORT=587
SMTP_USER=your-email@example.com
SMTP_PASSWORD=your-password
SMTP_FROM=booklore@example.com
```

## 🎮 Try the Demo

Before deploying, try the live demo at [demo.booklore.org](https://demo.booklore.org):

- **Username:** `booklore`
- **Password:** `9HC20PGGfitvWaZ1`

## 📚 Documentation

- [Official Website](https://booklore.org/)
- [Full Documentation](https://booklore.org/docs/getting-started)
- [GitHub Repository](https://github.com/booklore-app/booklore)
- [Discord Community](https://discord.gg/Ee5hd458Uz)

## 💜 Support BookLore

BookLore is free and open source. Support development:

- ⭐ [Star the GitHub repo](https://github.com/booklore-app/booklore)
- 💰 [Sponsor on Open Collective](https://opencollective.com/booklore)
- 📢 Share with friends and book lovers

## ⚖️ License

BookLore is licensed under the [GNU Affero General Public License v3.0](https://github.com/booklore-app/booklore/blob/develop/LICENSE).

---

**Note:** This template uses Railway's referral code for [matthewspear](https://github.com/matthewspear). Deploying supports both BookLore development and template maintenance.
