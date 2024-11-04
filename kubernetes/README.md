# Starting with Kubernetes

## Prerequisites

1. A Kubernetes cluster with a configured **kubectl** and a running ingress controller.
2. The domain `grafana.lan` must resolve to the address of your ingress controller.

## Configuration (Optional)

1. Open `kubernetes/configmap.yaml` with your preferred text editor.
2. Update the URL list in the `inputs.ping` plugin block to specify hosts and domains for which you want to collect ping statistics
   - **Example**: Replace `"192.168.1.1"` with the IP address of your router or a preferred local host. Add or remove hosts as needed.
3. Update the server list in the `inputs.dns_query` plugin block to specify DNS servers.
   - **Example**: Replace `"192.168.1.1"` with the IP address of your router or a preferred DNS server. Add or remove DNS servers as needed.
4. Update the domain list in the `inputs.dns_query` plugin block with the domains you want to track for DNS requests.
   - Add or remove domains as necessary.

## Starting 

1. Deploy and start the resources with the following command:
   ```bash
   kubectl apply -f kubernetes/
   ```
2. Check the rollout status of the application's pods using:
   ```bash
   kubectl get pods
   ```
3. Once all pods are in the **Running** state, open Grafana in your web browser: [http://grafana.lan](http://grafana.lan)
4. Follow these [instructions](https://github.com/androg9n/ispmonitor#using-the-grafana-web-interface-to-monitor-statistics) to use the Grafana web interface to monitor statistics.

## Stopping and Removing

1. To stop and remove all resources, use:
   ```bash
   kubectl delete -f kubernetes/
   ```

[🏠 Back to Main README](..)
