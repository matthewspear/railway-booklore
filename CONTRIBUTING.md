# Contributing to BookLore Railway Template

Thanks for your interest in improving this template! Here's how you can help.

## 🐛 Report Issues

Found a bug or have a suggestion?

1. Check [existing issues](../../issues) first
2. Open a new issue with:
   - Clear description of the problem
   - Steps to reproduce
   - Expected vs actual behavior
   - Railway logs (if applicable)

## 🔧 Submit Changes

### Setup for Development

1. **Fork and Clone**
   ```bash
   git clone https://github.com/YOUR-USERNAME/railway-booklore.git
   cd railway-booklore
   ```

2. **Test Locally with Docker Compose**
   ```bash
   cp .env.example .env
   # Edit .env with your settings
   docker compose up -d
   ```

3. **Access BookLore**
   - Open http://localhost:6060
   - Create an admin account
   - Test your changes

### Making Changes

1. **Create a Branch**
   ```bash
   git checkout -b fix/your-issue-name
   ```

2. **Make Your Changes**
   - Update `template.json` for Railway-specific config
   - Update `README.md` for documentation
   - Update `SETUP.md` for deployment guides
   - Test with `docker compose`

3. **Commit and Push**
   ```bash
   git add .
   git commit -m "Fix: your clear commit message"
   git push origin fix/your-issue-name
   ```

4. **Open a Pull Request**
   - Go to the original repository
   - Click "New Pull Request"
   - Select your fork and branch
   - Describe your changes

## 📋 Checklist Before Submitting

- [ ] Tested with `docker compose up`
- [ ] Updated README.md if needed
- [ ] Updated SETUP.md for new features
- [ ] No secrets/passwords in committed files
- [ ] Clear commit message
- [ ] Railway template JSON is valid

## 🎯 Areas to Contribute

### Documentation
- Improve setup instructions
- Add troubleshooting tips
- Document advanced configurations
- Add screenshots/GIFs

### Template Improvements
- Optimize resource usage
- Add new optional services
- Improve environment variable descriptions
- Add health checks

### Testing
- Test with different Railway plans
- Test volume persistence
- Verify database migrations
- Test custom domains

## 🔍 Testing Changes to Railway Template

### Local Testing
```bash
docker compose -f docker-compose.yml up -d
```

### Railway Testing
1. Fork this repository on GitHub
2. Deploy to Railway from your fork
3. Verify all services start correctly
4. Test environment variable substitution
5. Verify volumes persist after restart

## 📝 Commit Message Guidelines

Use clear, imperative messages:

- ✅ `Fix database connection timeout`
- ✅ `Add SMTP configuration guide`
- ✅ `Update BookLore to v1.5.0`
- ❌ `fixed stuff`
- ❌ `updates`

## 🤝 Code of Conduct

- Be respectful and inclusive
- Provide constructive feedback
- Help others learn and grow
- Focus on the issue, not the person

## 📚 Resources

- [Railway Docs](https://docs.railway.app/)
- [BookLore GitHub](https://github.com/booklore-app/booklore)
- [Docker Compose Docs](https://docs.docker.com/compose/)
- [Railway Templates Guide](https://docs.railway.app/reference/templates)

## 💜 Thank You!

Every contribution helps make this template better for the community. We appreciate your time and effort!

---

**Questions?** Open an issue or reach out on the [BookLore Discord](https://discord.gg/Ee5hd458Uz).
