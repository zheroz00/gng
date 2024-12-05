# GNG System Architecture 🚀

## Quick Start Guide 🎯

Hey there! This is your friendly neighborhood system guide. Here's what we've got cooking:

### The Big Picture 🖼️

We've split everything into nice, tidy containers that all work together:

```
📦 GNG System
├── 🛠️ Infrastructure
│   ├── MinIO (file storage)
│   └── Redis (caching)
├── 🗄️ Databases
│   ├── NocoDB System DB (PostgreSQL)
│   └── Business Data DB (PostgreSQL)
└── 📱 Apps
    └── NocoDB (low-code platform)
```

### How to Start Everything 🎬

1. Start the whole system:
   ```bash
   docker compose up -d
   ```

2. Access NocoDB:
   - Open browser: `http://localhost:8080`
   - Default port: 8080

### Container Names at a Glance 👀

- `gng-minio`: File storage
- `gng-redis`: Caching
- `gng-nocodb_system_db`: NocoDB system database
- `gng-business_data_db`: Your business data
- `gng-nocodb`: The NocoDB application

---

## Function Map 🗺️

### System Path Reference 📍
Absolute path to workspace root: `/mnt/dockerSSD/git/gng`

### Directory Structure
```
root/
├── apps/
│   └── nocodb/
│       ├── docker-compose.yml  # NocoDB app configuration
│       └── data/              # NocoDB data storage
├── databases/
│   ├── docker-compose.yml     # Database services
│   ├── nocodb_system/        # System DB data
│   └── business_data/        # Business DB data
├── infrastructure/
│   ├── docker-compose.yml    # MinIO and Redis config
│   ├── minio/               # MinIO data
│   └── redis/              # Redis data
└── docker-compose.yml       # Master compose file
```

### Key Configuration Files 📝

1. Database Connections:
   - Main config: `apps/nocodb/docker-compose.yml`
   - Environment variables:
     ```
     NC_DB: Points to gng-nocodb_system_db
     NC_DATA_DB: Points to gng-business_data_db
     ```

2. Storage Configuration:
   - MinIO setup: `infrastructure/docker-compose.yml`
   - Redis cache: `infrastructure/docker-compose.yml`

### Network Configuration 🌐

- All services connect through: `n8n_network`
- Network type: External
- Defined in: All docker-compose.yml files

### Data Persistence 💾

- Database data:
  - System DB: `databases/nocodb_system/data`
  - Business DB: `databases/business_data/data`
- File storage:
  - MinIO: `infrastructure/minio/data`
  - Redis: `infrastructure/redis/data`
- App data:
  - NocoDB: `apps/nocodb/data`

### Service Dependencies 🔄

1. Infrastructure (Start First):
   - MinIO
   - Redis

2. Databases (Start Second):
   - nocodb_system_db
   - business_data_db

3. Applications (Start Last):
   - NocoDB

### Troubleshooting Quick Reference 🔧

1. Database Connection Issues:
   - Check container names in `apps/nocodb/docker-compose.yml`
   - Verify network connectivity
   - Ensure databases are running first

2. Data Persistence Issues:
   - Check volume mappings in respective docker-compose files
   - Verify directory permissions

3. Service Discovery Issues:
   - Ensure all services are on `n8n_network`
   - Verify container names match configuration