## Usage

[Helm](https://helm.sh) must be installed to use the charts.  Please refer to
Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

  helm repo add <alias> https://leogsilva.github.io/charts

If you had already added this repo earlier, run `helm repo update` to retrieve
the latest versions of the packages.  You can then run `helm search repo
<alias>` to see the charts.

To install the syntropy-agent chart:

    helm install my-agent leogsilva/syntropy-agent

To uninstall the chart:

    helm delete my-agent

## Syntropy specific values
If you need to customize the helm installation, there are important values that must be add to values.yaml

```yaml
syntropy:
  token: ZLJS1b48yLHPkYLQDXCRsAskA 
  allowed_ips: |
          "[{\"0.0.0.0/0\":\"internet\"}]"
  ip_from: "eth0"
  namespaces: "demo"
  name: "u1"
  tags: "pod_cidr:10.1.0.0/16,service_cidr:100.1.0.0/16,submariner-master"
  network: 1400
  apiServer: "https://controller-prod-server.syntropystack.com"
  apiToken: "WDJOZVZiMnZlMT1hEVSVEeQ=="
```

* token: a valid syntropy agent token. You can obtain one [here](https://docs.syntropystack.com/docs/get-your-agent-token).
* allowed_ips: list of allowed ips to be added to wireguard interface
* ip_from: interface used for outbound traffic
* name: the name of the agent on syntropy stack
* tags: mandatory tags to identify submariner clusters. 
```
pod_cidr:x.x.x.x/x // kubernetes cluster pod cidr
```
```
service_cidr: x.x.x.x/x // kubernetes cluster service cidr
```
```
global_ip:x.x.x.x/32 // kubernetes ip to be used as health checker
```
```
submariner-master / submariner-node // the role of the kubernetes cluster in the mesh
```
* network: id of the network on syntropy stack that configures the mesh (all kubernetes clusters inside the same network)

* apiServer: syntropy stack api endpoint
* apiToken: valid api token obtained [here](https://docs.syntropystack.com/docs/access-tokens)
