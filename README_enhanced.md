
# Checkmk Monitoring Solution

## Overview

Checkmk is a powerful IT monitoring solution that helps you monitor your entire IT infrastructure. This repository contains the setup for a Checkmk monitoring solution using Docker, allowing you to deploy a scalable and customizable monitoring environment with ease.

## Features

- **Comprehensive Monitoring**: Monitor servers, networks, applications, cloud environments, and more.
- **Scalability**: Easily scale your monitoring infrastructure to handle thousands of hosts and services.
- **User-Friendly Interface**: Intuitive web interface with customizable dashboards.
- **Alerting and Notifications**: Get alerts and notifications based on custom rules and thresholds.
- **Extendable**: Supports custom plugins and integrations for various tools and platforms.

## Architecture Diagram

Below is a high-level architecture of the Checkmk setup using Docker Compose:

```
+------------------+       +----------------+
|   User Browser   | <---> |   Checkmk Web  |
+------------------+       |   Interface    |
                           +----------------+
                                  |
                         Docker Network (checkmk_network)
                                  |
+-----------------------------------------------+
|               Checkmk Docker Container        |
|   (checkmk/check-mk-cloud:latest image)       |
|                                               |
| - Exposed Ports: 5000 (Web UI), 8000 (API)    |
| - Persistent Volume: monitoring_data          |
| - Health Checks and Resource Limits Configured|
+-----------------------------------------------+
```

## Prerequisites

- Docker installed on your system.
- Docker Compose installed.
- Basic knowledge of Docker and Checkmk.

## Installation Steps

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/amrmarey/checkmk.git
   cd checkmk
   ```

2. **Configure Environment Variables**:
   Create a `.env` file in the root directory with the following contents or use the provided `.env` template:
   ```bash
   CHECKMK_PORT=5000
   CHECKMK_REGISTER_PORT=8000
   CMK_SITE_ID=mysite
   CMK_PASSWORD=yourpassword
   ```

3. **Deploy Checkmk with Docker Compose**:
   Run the following command to start the Checkmk container:
   ```bash
   docker-compose up -d
   ```

   This will start the Checkmk container in detached mode.

## Configuration

- **Site ID**: Set in the `.env` file as `CMK_SITE_ID`.
- **Password**: Set in the `.env` file as `CMK_PASSWORD`.
- **Ports**: Configured in the `.env` file:
  - `CHECKMK_PORT` (default: 5000)
  - `CHECKMK_REGISTER_PORT` (default: 8000)

## Advanced Configuration

- **Scaling**: Modify `docker-compose.yml` to scale the number of replicas if needed.
- **Custom Plugins**: Mount custom plugins or configurations by adding volume mounts to the `docker-compose.yml` file.
- **Resource Optimization**: Adjust CPU and memory limits in the `docker-compose.yml` under the `deploy` section.

## Screenshots

Include screenshots of the Checkmk web interface, configuration screens, and sample dashboards to help users understand the interface better.

## Troubleshooting

- **Container Not Starting**: Check Docker logs using `docker logs monitoring`.
- **Health Check Failures**: Ensure ports `5000` and `8000` are not in use by other services.
- **Configuration Changes**: After making changes to the `.env` file or `docker-compose.yml`, run `docker-compose down && docker-compose up -d` to apply the changes.

## Support

For support, please refer to the [Checkmk Documentation](https://docs.checkmk.com/) or open an issue in this repository.

## Contributing

Contributions are welcome! To contribute, please follow these steps:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Commit your changes (`git commit -m 'Add new feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Open a Pull Request.

Ensure your code follows the style guidelines and includes necessary documentation and tests.

## License

This project is licensed under the MIT License.
