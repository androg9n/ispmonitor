# ISP Monitoring Service

A simple service to monitor the quality of internet resource accessibility from your host. This tool uses `ping` to gather measurable metrics, collects them, and presents a useful visual dashboard.

![ISP Monitoring Dashboard Screenshot](images/Screenshot1.png "ISP Monitoring Dashboard Screenshot")

[Screenshot1](images/Screenshot1.png)
[Screenshot2](images/Screenshot2.png)
[Screenshot3](images/Screenshot3.png)

## How It Works

- **Telegraf** - Executes automated `ping` requests to configured URLs and hosts. Shares gathered metrics via an HTTP endpoint.
- **Prometheus** - Scrapes metrics from the Telegraf service and organizes them using labeled structures.
- **Grafana** - Pulls metrics from Prometheus and builds a dashboard for visual insights.

## Bringing Code onto Your Host

1. Ensure you have Git or another tool to clone repositories. [Download Git here](https://git-scm.com/downloads).
2. Clone the `ispmonitor` code to your host:
   - Prepare a directory for the code.
   - Open a terminal in this directory.
   - Run the clone command:
     ```bash
     git clone git@github.com:androg9n/ispmonitor.git
     ```
   - Navigate into the directory with the cloned code:
     ```bash
     cd ispmonitor
     ```
## Configuration

1. Open the file `ispmonitor-telegraf.conf` with your preferred text editor.
2. Update the URL list in the `inputs.ping` plugin block to specify hosts and domains for which you want to collect ping statistics.
   - **Example**: Replace `"192.168.1.1"` with your router's IP or a preferred local host. Add or remove hosts as needed.
3. Update the server list in the `inputs.dns_query` plugin block to specify DNS servers.
   - **Example**: Replace `"192.168.1.1"` with your router's IP or preferred DNS server. Add or remove DNS servers as needed.
4. Update the domain list in the `inputs.dns_query` plugin block with the domains you want to track for DNS requests.
   - Add or remove domains as necessary.

## Starting with Docker Compose

Docker Compose provides a universal platform to run containerized services on any host.

## Starting with Docker Compose

Docker Compose provides a universal platform to run containerized services on any host.

1. Ensure Docker Compose is installed on your host. [Installation instructions](https://docs.docker.com/compose/install/).
2. Open a terminal in the `ispmonitor` code directory.
3. Navigate to the `docker-compose` directory:
   ```bash
   cd docker-compose 
   ```
4. Start the services with the command: `docker compose up -d`.
   ```bash
   docker compose up -d
   ```
5. Open the Grafana web interface (see instructions below).
5. To stop the services, run from the `docker-compose` directory:
   ```bash
   docker compose down
   ```
6. To delete all collected service data, run from the same directory:
   ```bash
   docker compose down -v
   ```

## Using the Grafana Web Interface to Monitor Statistics

1. Open Grafana in your web browser using your host's address on port 3000. For a local setup, go to: [http://localhost:3000](http://localhost:3000).
2. Upon your first login, use the default username and password: **admin/admin**. You will be prompted to set a new password.
3. On the Welcome page, access the ISP Monitoring dashboard from the bottom left corner or by navigating to **Dashboards > ISP Monitoring** in the main menu.
4. If statistics don’t appear immediately, wait 30 seconds or use the Refresh button in the top-right corner.
5. Use the **Variables** bar (top-left corner) and **Time Range** (top-right corner) to customize the dashboard visualizations.
