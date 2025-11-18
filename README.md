# Home Lab Service Dashboard

A simple, responsive dashboard for managing and accessing self-hosted services in your home lab. This project provides a central hub to organize and link to all your running applications.

_Design inspired by the classic Apache2 default landing page._

## Features

- **Service Grid:** Displays all configured services with name, favicon, and URL.
- **Responsive Design:** Works well on desktop and mobile devices.
- **Easy Configuration:** Add or remove services via `config.json`.
- **Optional Admin Info:** You can add an optional `support` email or admin contact for your dashboard in `config.json`.
- **Static Hosting:** Ready for deployment on GitHub Pages or any static web server.

## Getting Started

### Option 1: Docker (Recommended)

1. **Clone the repository:**

   ```sh
   git clone https://github.com/cswitenky/homelab-dashboard.git
   cd homelab-dashboard
   ```

2. **Edit your config.json:**

   - Modify `config.json` with your services:
     ```json
     {
       "support": "support@example.com",
       "services": [
         {
           "name": "Plex",
           "url": "https://plex.example.com"
         },
         {
           "name": "Home Assistant",
           "url": "https://homeassistant.example.com"
         }
       ]
     }
     ```

3. **Run with Docker Compose:**

   ```sh
   docker-compose up -d
   ```

   The dashboard will be available at http://localhost:8080

4. **Or run with Docker directly:**

   ```sh
   # Build the image
   docker build -t homelab-dashboard .

   # Run the container with your config.json mounted
   docker run -d \
     -p 8080:80 \
     -v $(pwd)/config.json:/usr/share/nginx/html/config.json:ro \
     --name homelab-dashboard \
     homelab-dashboard
   ```

### Option 2: Static Hosting

1. **Clone the repository:**

   ```sh
   git clone https://github.com/cswitenky/homelab-dashboard.git
   ```

2. **Add your services:**

   - Edit `config.json` and add your service entries. You may also include an optional `support` field for admin contact:
     ```json
     {
       "support": "support@example.com",
       "services": [
         {
           "name": "Example",
           "url": "https://example.com"
         }
       ]
     }
     ```

3. **Open the dashboard:**
   - Open `index.html` in your browser, or deploy to any static web server.

## Docker Configuration

The Docker setup uses nginx to serve the static files. The `config.json` file is mounted as a volume, allowing you to update your services without rebuilding the container.

### Environment Variables

The container exposes port 80. You can map it to any host port:

```sh
docker run -d -p 3000:80 -v $(pwd)/config.json:/usr/share/nginx/html/config.json:ro homelab-dashboard
```

### Updating Services

To update your services, simply edit `config.json` and refresh your browser. No container restart required!

## Deployment

### GitHub Pages

This project includes a GitHub Actions workflow (`.github/workflows/static.yml`) for automatic deployment to GitHub Pages.

### Docker Hub

You can also push the image to Docker Hub for easy deployment across your infrastructure.
