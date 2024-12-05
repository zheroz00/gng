# GNG Docker Environment 🚀

A modular Docker-based development environment featuring NocoDB with separate system and business databases, along with MinIO for file storage and Redis for caching.

## Features ✨

- **Modular Structure**: Organized into infrastructure, databases, and applications
- **Scalable Design**: Each service is independently configurable and maintainable
- **Data Persistence**: Properly configured volume mappings for all services
- **Network Isolation**: All services communicate through a dedicated network

## Quick Start 🎯

1. Clone the repository:
   ```bash
   git clone https://github.com/zheroz00/gng.git
   cd gng
   ```

2. Create a `.env` file with your configuration (see `.env.example` for reference)

3. Start the services:
   ```bash
   docker compose up -d
   ```

4. Access NocoDB:
   - URL: `http://localhost:8080`

## Architecture 🏗️

The system is divided into three main components:

- **Infrastructure**: MinIO (file storage) and Redis (caching)
- **Databases**: Separate PostgreSQL instances for system and business data
- **Applications**: NocoDB as the primary application

For detailed architecture information, see [System Architecture](docs/system_architecture.md).

## Directory Structure 📁

```
root/
├── apps/              # Application services
├── databases/         # Database services
├── infrastructure/    # Infrastructure services
└── docs/             # Documentation
```

## Maintenance 🔧

- Each service has its own `docker-compose.yml` file for independent management
- Data persistence is handled through Docker volumes
- Logs are available in the respective service directories

## Contributing 🤝

Feel free to submit issues and enhancement requests!

## License 📄

[MIT](LICENSE)

---
Made with ❤️ using Docker and NocoDB 