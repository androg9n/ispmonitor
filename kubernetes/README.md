# Starting with Kubernetes

## Prerquisites

1. Kubernates cluster, configured **kubectl**, running ingress conroller
2. Domain `grafana.lan` must resolve address of your ingress controller

## Configuration (Optional)

1. Open the file `kubernetes/configmap.yaml` with your preferred text editor
2. Update the URL list in the `inputs.ping` plugin block to specify hosts and domains for which you want to collect ping statistics
   - **Example**: Replace `"192.168.1.1"` with your router's IP or a preferred local host. Add or remove hosts as needed
3. Update the server list in the `inputs.dns_query` plugin block to specify DNS servers
   - **Example**: Replace `"192.168.1.1"` with your router's IP or preferred DNS server. Add or remove DNS servers as needed
4. Update the domain list in the `inputs.dns_query` plugin block with the domains you want to track for DNS requests
   - Add or remove domains as necessary

## Starting 

1. Deploy and start the resources with the command:
   ```bash
   kubectl apply -f kubernetes/
   ```
2. Control rollout of application's pods by STATUS using command:
   ```bash
   kubectl get pods
   ```
3. After all pods are **Running** open Grafana in your web browser: [http://grafana.lan](http://grafana.lan)
4. Follow [instructions](https://github.com/androg9n/ispmonitor#using-the-grafana-web-interface-to-monitor-statistics) to use Grafana Web Interface to Monitor Statistics

## Stopping and removing

1. To stop and remove all resources:
   ```bash
   kubectl delete -f kubernetes/
   ```
