# Example usage

Read through the below before you deploy this module.

- [Prerequisites](#prerequisites)
- [How to deploy](#how-to-deploy)
- [After it's successfully deployed](#after-its-successfully-deployed)

## Prerequisites

This module expects that you already own or create the below resources yourself.

- Google network, subnetwork and a Cloud NAT
- Service account, [specifics can be found here](../../README.md#service-account)
- Domain, [specifics can be found here](../../README.md#dns-record)
- The following firewall rules configured in the host network:
  - Allow IAP access (<https://cloud.google.com/iap/docs/using-tcp-forwarding#create-firewall-rule>)
    - source ip ranges: `[35.235.240.0/20]`
    - target tags: `[allow-iap]`
    - tcp, port 22
  - Allow load balancer healthchecks: (<https://cloud.google.com/load-balancing/docs/health-checks#fw-rule>)
    - source ip ranges: `[130.211.0.0/22, 35.191.0.0/16]`
    - target tags `[allow-lb-health-checks]`
    - tcp

If you prefer an example that includes the above resources, see [`complete example`](https://github.com/bschaatsbergen/atlantis-on-gcp-vm/tree/master/examples/complete).

## How to deploy

See [`main.tf`](https://github.com/bschaatsbergen/atlantis-on-gcp-vm/tree/master/examples/basic/main.tf) and the [`server-atlantis.yaml`](https://github.com/bschaatsbergen/atlantis-on-gcp-vm/tree/master/examples/basic/server-atlantis.yaml).

## After it's successfully deployed

Once you're done, see [Configuring Webhooks for Atlantis](https://www.runatlantis.io/docs/configuring-webhooks.html#configuring-webhooks)
