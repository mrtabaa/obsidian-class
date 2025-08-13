### Development

1. Install PostgreSQL server
```bash
sudo apt install postgresql
```

2. Setup superuser password
```bash
sudo -i -u postgres

psql

\password
```

3. Install DBeaver as a GUI: [download](https://dbeaver.io/download/)

4. Create your databases under `postgres` user. 

5. Connection to the project
```json
"PostgresConnectionString": "Host=localhost;Port=5432;Database=MY_PROJECT;Username=postgres;Password=MY_PASSWPRD;Pooling=true;Minimum Pool Size=5;Maximum Pool Size=100;SSL Mode=Disable",
```

### Production

1. The `postgres` user is a **superuser** and **unsafe** to be used on **production**. We must create another user with **less privileges** on production. 

2. Connection to the project
```json
"PostgresConnectionString": 
"Host=localhost;Port=5432;Database=MY_PROJECT;Username=MY_LIMITED_USER;Password=STRONG_PASSWORD;Pooling=true;Minimum Pool Size=10;Maximum Pool Size=50;SSL Mode=Require;Trust Server Certificate=false"
```

**Changes made for production:**
- `Pooling=true` → Enables **connection pooling** so EF/Dapper can reuse open DB connections instead of reconnecting every time (big performance gain).
- `Minimum Pool Size=10` → Keep at least **10 connections** alive in the pool at all times.
- `Maximum Pool Size=50` → Limit pool to **100 concurrent connections** to avoid overloading the DB.
- `SSL Mode=Require` → Forces TLS encryption for in-transit data security.
- `Trust Server Certificate=false` → Ensures the certificate is validated (prevents MITM attacks).