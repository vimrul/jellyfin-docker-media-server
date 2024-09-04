
# Jellyfin Docker Setup

This repository contains a `docker-compose.yml` file to set up a Jellyfin media server with Docker. Jellyfin is a free and open-source media server software that allows you to stream your media files from anywhere.

## Prerequisites

- Docker and Docker Compose installed on your host machine.
- User ID (PUID) and Group ID (PGID) to ensure the correct permissions for Jellyfin.
- Host machine paths for media files (movies, TV shows, music, photos, audiobooks).

## Setup

### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/jellyfin-docker-setup.git
cd jellyfin-docker-setup
```

### 2. Modify the `docker-compose.yml` File

Replace the `/path/to/` placeholders in the `volumes` section with the actual paths to your media locations on your host machine:

- `/path/to/config:/config`: Stores Jellyfin configuration files.
- `/path/to/cache:/cache`: Stores cache files for Jellyfin.
- `/path/to/media1:/media/movies`: Path to your movie files.
- `/path/to/media2:/media/tv`: Path to your TV show files.
- `/path/to/media3:/media/music`: Path to your music files.
- `/path/to/media4:/media/photos`: Path to your photo files.
- `/path/to/media5:/media/audiobooks`: Path to your audiobook files.

You can find your PUID and PGID by running the following commands:

- **Find PUID**: `id -u`
- **Find PGID**: `id -g`

Update the `PUID`, `PGID`, and `TZ` (timezone) environment variables in the `docker-compose.yml` file.

### 3. Run the Jellyfin Container

Once you have updated the `docker-compose.yml` file with your configuration, you can run the Jellyfin container by executing:

```bash
docker-compose up -d
```

This will start Jellyfin as a background service.

### 4. Access Jellyfin

After the container is running, you can access Jellyfin from your browser:

- **URL**: `http://localhost:8096` for the standard connection
- **URL**: `https://localhost:8920` for the HTTPS connection

### 5. Stopping the Container

To stop the Jellyfin container, run:

```bash
docker-compose down
```

### 6. Updating Jellyfin

To update Jellyfin to the latest version, pull the latest image and recreate the container:

```bash
docker-compose pull
docker-compose up -d
```

## docker-compose.yml Overview

```yaml
version: '3.8'

services:
  jellyfin:
    image: jellyfin/jellyfin:latest
    container_name: jellyfin
    restart: unless-stopped
    ports:
      - "8096:8096"
      - "8920:8920" # for HTTPS
    environment:
      - PUID=1000 # change this to your user id
      - PGID=1000 # change this to your group id
      - TZ=Asia/Dhaka # change this to your timezone
    volumes:
      - /path/to/config:/config
      - /path/to/cache:/cache
      - /path/to/media1:/media/movies
      - /path/to/media2:/media/tv
      - /path/to/media3:/media/music
      - /path/to/media4:/media/photos
      - /path/to/media5:/media/audiobooks

networks:
  default:
    driver: bridge
    environment:
      - JELLYFIN_PublishedServerUrl=http://example.com
    extra_hosts:
      - 'host.docker.internal:host-gateway'
```

## License

This project is licensed under the MIT License.

## Contributions

Contributions are welcome! Feel free to open an issue or submit a pull request.

## Author

[Imrul](https://imrul.net)

## Contact

For any inquiries, please contact me at [hello@imrul.net](mailto:hello@imrul.net).
