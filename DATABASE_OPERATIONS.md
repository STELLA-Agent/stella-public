# Database Operations Guide

## Connect to Database

Both development and production use **Google Cloud SQL**, just different databases.

### Development Environment (Cloud SQL via Proxy)
```bash
# Start Cloud SQL Proxy (if not already running)
cloud_sql_proxy --port 5432 semiotic-sylph-470501-q5:us-central1:stella-db

# Connect to development database
psql "host=localhost port=5432 dbname=stella_chat_dev user=stella-user"
```

### Production Environment (Cloud SQL)

#### Method 1: Cloud SQL Proxy
```bash
# Start proxy on different port to avoid conflict
cloud_sql_proxy --port 5433 semiotic-sylph-470501-q5:us-central1:stella-db

# Connect to production database
psql "host=127.0.0.1 port=5433 dbname=stella_chat user=stella-user sslmode=disable"
```

#### Method 2: Cloud Console SQL Editor
1. Go to Google Cloud Console
2. SQL → stella-db → SQL Editor
3. Run SQL directly

## Update Schema

### Add Column
```sql
ALTER TABLE table_name 
ADD COLUMN IF NOT EXISTS column_name TYPE;
```

### Modify Column
```sql
ALTER TABLE table_name 
ALTER COLUMN column_name TYPE new_type;
```

### Drop Column
```sql
ALTER TABLE table_name 
DROP COLUMN IF EXISTS column_name;
```

## Common Queries

### View Table Structure
```sql
\d table_name
```

### List All Tables
```sql
\dt
```

### View Column Information
```sql
SELECT column_name, data_type, character_maximum_length
FROM information_schema.columns 
WHERE table_name = 'table_name';
```

## Python Script Approach

Create `sync_schema.py`:
```python
import asyncio
import asyncpg
import os

async def update_schema():
    # Connect via Cloud SQL Proxy
    conn = await asyncpg.connect(
        host='127.0.0.1',
        port=5433,  # Production proxy port
        user='stella-user',
        password=os.getenv('DB_PASSWORD'),
        database='stella_chat'  # or stella_chat_dev for dev
    )
    
    await conn.execute('YOUR SQL HERE')
    await conn.close()

asyncio.run(update_schema())
```

Run:
```bash
python sync_schema.py
```

## Important Notes

- ⚠️ Test in development environment before production
- ✅ Use `IF NOT EXISTS` / `IF EXISTS` for idempotency
- 🔒 Read database password from environment variables
- 📝 Backup before important operations

## Environment Variables

```bash
# .env file (DO NOT commit to git)
DB_PASSWORD=your-password-here
DB_USER=stella-user
```

