# Web Server

This directory covers the deployment of a vulnerable web application used as a target system for the Wazuh Home Lab.

The web server is built using Docker and consists of:

- **NGINX** – Acts as a reverse proxy and generates web server access and error logs.
- **OWASP Juice Shop** – An intentionally vulnerable web application used for security testing and attack simulation.

The generated logs are collected by the Wazuh Agent and forwarded to the Wazuh Server for monitoring, threat detection, and analysis.

---

## Architecture

```text
                Internet / LAN
                       │
                       ▼
                 NGINX Proxy
                 (Port 80/443)
                       │
          Docker Bridge Network
                       │
                       ▼
              OWASP Juice Shop
                 (Port 3000)
```

> **Note**
>
> Juice Shop is **not exposed directly** to the local network. All client requests pass through the NGINX reverse proxy.

---

## Directory Structure

```
Web-Server/
│
├── README.md
├── Docker-Installation.md
└── Web-Server-Setup.md
```

---

## Roadmap

Follow the documents in the following order:

1. Install Docker Engine and Docker Compose.
2. Deploy the NGINX reverse proxy and Juice Shop using Docker Compose.
3. Verify that the web application is accessible through NGINX.
4. Confirm that NGINX access and error logs are generated.
5. Install and configure the Wazuh Agent.

---

## What You'll Learn

After completing this section, you will be able to:

- Install Docker on Debian.
- Deploy multiple containers using Docker Compose.
- Configure NGINX as a reverse proxy.
- Isolate backend services from the local network.
- Generate realistic web server logs.
- Prepare the web server for centralized log collection using Wazuh.

---

## References

- Docker Engine Installation (Debian): https://docs.docker.com/engine/install/debian/
- Docker Compose Documentation: https://docs.docker.com/compose/
- OWASP Juice Shop Docker Image: https://hub.docker.com/r/bkimminich/juice-shop
- NGINX Official Docker Image: https://hub.docker.com/_/nginx
