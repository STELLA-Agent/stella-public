# Stella AI - Public Documentation

Public documentation and operation guides.

## 📄 Documentation

### **DATABASE_OPERATIONS.md**
General guide for database connections and operations

**Includes:**
- Development and production connection methods
- Schema update operations
- Common SQL commands
- Python script examples

### **logo/**
Brand assets

---

## 🔐 Security Notes

**⚠️ IMPORTANT:** This folder should NOT contain:
- Database passwords
- API keys
- Email credentials
- Auth0 secrets
- Any sensitive configuration

All sensitive data should be stored in:
- `.env` files (gitignored)
- Google Cloud Secret Manager
- Cloud Run environment variables

