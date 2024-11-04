#Kube-router is a turnkey solution for Kubernetes networking with aim to provide operational simplicity and high performance.

![](https://i.imgur.com/waxVImv.png)
### [View all Roadmaps](https://github.com/nholuongut/all-roadmaps) &nbsp;&middot;&nbsp; [Best Practices](https://github.com/nholuongut/all-roadmaps/blob/main/public/best-practices/) &nbsp;&middot;&nbsp; [Questions](https://www.linkedin.com/in/nholuong/)
<br/>

## Primary Features

*kube-router does it all.*

With all features enabled, kube-router is a lean yet powerful alternative to
several network components used in typical Kubernetes clusters. All this from a
single DaemonSet/Binary. It doesn't get any easier.

### IPVS/LVS based service proxy | `--run-service-proxy`

kube-router uses the Linux kernel's LVS/IPVS features to implement its K8s Services Proxy. Kube-router fully leverages
power of LVS/IPVS to provide a rich set of scheduling options and unique features like DSR (Direct Server Return), L3
load balancing with ECMP for deployments where high throughput, minimal latency and high-availability are crucial.

### Pod Networking | `--run-router`

kube-router handles Pod networking efficiently with direct routing thanks to the BGP protocol and the GoBGP Go library.
It uses the native Kubernetes API to maintain distributed pod networking state. That means no dependency on a separate
datastore to maintain in your cluster.

kube-router's elegant design also means there is no dependency on another CNI
plugin. The
[official "bridge" plugin](https://github.com/containernetworking/plugins/tree/master/plugins/main/bridge)
provided by the CNI project is all you need. While it is likely that you already have this plugin on your file system
if you've installed Kubernetes, kube-router will install the plugins it needs for you in `/opt/cni/bin` if it sees
you're missing them.

### Network Policy Controller | `--run-firewall`

Enabling Kubernetes [Network Policies](https://kubernetes.io/docs/concepts/services-networking/network-policies/)
is easy with kube-router -- just add a flag to kube-router. It uses ipsets with
iptables to ensure your firewall rules have as little performance impact on your
cluster as possible.

Kube-router supports the networking.k8s.io/NetworkPolicy API or network policy V1/GA
[semantics](https://github.com/kubernetes/kubernetes/pull/39164#issue-197243974) and also network policy beta semantics.

### Advanced BGP Capabilities

If you have other networking devices or SDN systems that talk BGP, kube-router will fit in perfectly. From a simple full
node-to-node mesh to per-node peering configurations, most routing needs can be attained. The configuration is
Kubernetes native (annotations) just like the rest of kube-router, so use the tools you already know! Since kube-router
uses GoBGP, you have access to a modern BGP API platform as well right out of the box. Kube-router also provides a way
to expose services outside the cluster by advertising ClusterIP and externalIPs to configured BGP peers. Kube-routesalso
support MD5 password based authentication and uses strict export policies so you can be assured routes are advertised to
the underlay only as you intended.

For more details please refer to the [BGP documentation](docs/bgp.md).

### Standard Linux Networking

A key design tenet of Kube-router is to use standard Linux networking stack and toolset. There is no overlays or SDN
pixie dust, but just plain good old networking. You can use standard Linux networking tools like iptables, ipvsadm,
ipset, iproute, traceroute, tcpdump etc. to troubleshoot or observe data path. When kube-router is ran as a daemonset,
the official kube-router image also ships with these [tools](./docs/pod-toolbox.md#pod-toolbox) automatically configured
for your cluster.

### Small Footprint

Although it does the work of several of its peers in one binary, kube-router does it all with a relatively
[tiny codebase](https://github.com/nholuongut/kube-router/tree/master/pkg/controllers), partly because IPVS is
already there on your Kuberneres nodes waiting to help you do amazing things. kube-router brings that and GoBGP's modern
BGP interface to you in an elegant package designed from the ground up for Kubernetes.

### High Performance

A primary motivation for kube-router is performance. The combination of BGP for inter-node Pod networking and IPVS for
load balanced proxy Services is a perfect recipe for high-performance cluster networking at scale. BGP ensures that the
data path is dynamic and efficient, and IPVS provides in-kernel load balancing that has been thoroughly tested and
optimized.

## Getting Started

- [How it Works](./docs/how-it-works.md)
- [Architecture](./docs/architecture.md)
- [See Kube-router in action](./docs/see-it-in-action.md)
- [User Guide](./docs/user-guide.md)
- [Developer Guide](./docs/developing.md)

## Project status

Kube-router is being used in several production clusters by diverse set of users ranging from financial firms, gaming
companies to universities. For years we have listened to users and incorporated feedback. The core functionality is now
very stable.

## Contributing

We encourage all kinds of contributions, be they documentation, code, fixing
typos, tests — anything at all. Please read the [contribution guide](./CONTRIBUTING.md).

# 🚀 I'm are always open to your feedback.  Please contact as bellow information:
### [Contact ]
* [Name: Nho Luong]
* [Skype](luongutnho_skype)
* [Github](https://github.com/nholuongut/)
* [Linkedin](https://www.linkedin.com/in/nholuong/)
* [Email Address](luongutnho@hotmail.com)
* [PayPal.me](https://www.paypal.com/paypalme/nholuongut)

![](https://i.imgur.com/waxVImv.png)
![](Donate.png)
[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/nholuong)

# License
* Nho Luong (c). All Rights Reserved.🌟

