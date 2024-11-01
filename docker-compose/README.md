# Starting with Docker Compose

##Prerquisites

1. Docker Compose is installed on your host. [Installation instructions](https://docs.docker.com/compose/install/).

## Configuration (Optional)

1. Open the file `docker-compose/ispmonitor-telegraf.conf` with your preferred text editor.
2. Update the URL list in the `inputs.ping` plugin block to specify hosts and domains for which you want to collect ping statistics
   - **Example**: Replace `"192.168.1.1"` with your router's IP or a preferred local host. Add or remove hosts as needed
3. Update the server list in the `inputs.dns_query` plugin block to specify DNS servers
   - **Example**: Replace `"192.168.1.1"` with your router's IP or preferred DNS server. Add or remove DNS servers as needed
4. Update the domain list in the `inputs.dns_query` plugin block with the domains you want to track for DNS requests
   - Add or remove domains as necessary

## Starting, stopping, removing 

1. Open a terminal in the `ispmonitor` code directory.
2. Navigate to the `docker-compose` directory:
   ```bash
   cd docker-compose 
   ```
3. Start the services with the command: `docker compose up -d`.
   ```bash
   docker compose up -d
   ```
4. Open Grafana in your web browser using your host's address on port 3000. For a local setup, go to: [http://localhost:3000](http://localhost:3000)
5. Follow the [instructions](https://github.com/androg9n/ispmonitor#using-the-grafana-web-interface-to-monitor-statistics) to use Grafana Web Interface to Monitor Statistics

## Stopping and removing

1. To stop the services, run from the `docker-compose` directory:
   ```bash
   docker compose down
   ```
2. To delete all collected service data, run from the same directory:
   ```bash
   docker compose down -v
   ```

