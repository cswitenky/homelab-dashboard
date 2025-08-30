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

1. **Clone the repository:**

   ```sh
   git clone https://github.com/cswitenky/homelab-dashboard.git
   ```

2. **Add your services:**

   - Edit `config.json` and add your service entries. You may also include an optional `support` field for admin contact:
     ```json
     {
       "support": "support@example.com", // optional admin info
       "services": [
         {
           "name": "Example",
           "url": "https://example.com"
         },
         {
           "name": "Example Org",
           "url": "https://example.org"
         },
         {
           "name": "Example Net",
           "url": "https://example.net"
         },
         {
           "name": "IANA Reserved",
           "url": "https://iana.org"
         },
         {
           "name": "W3C",
           "url": "https://w3.org"
         }
       ]
     }
     ```

3. **Open the dashboard:**
   - Open `index.html` in your browser.

## Deployment

This project includes a GitHub Actions workflow (`.github/workflows/static.yml`) for automatic deployment to GitHub Pages.
