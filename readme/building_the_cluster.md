<p align="center">
  <img height="200" title="Kubernetes Logo" src="images/k8s_logo_with_border.png">
</p>

# Setting up your Kubernetes Sandbox

For low-cost, easy-to-deploy sandboxing, I suggest using k3s. k3s is a lightweight production-grade Certified Kubernetes distribution. More info can be found at https://k3s.io/.

You can set up k3s on multiple platforms:

## Set up k3s on MacOS:

The first option is to set up k3s locally on your MacOS machine. The benefit here is that it is very easy to deploy a frech cluster whenever you wish. The tradeoff here is that external connections to k3s objects (services, ingress) are not supported.

You will need three components to deploy and manage a local MacOS-based k3s cluster:

- VirtualBox: a free and open-source hosted hypervisor for x86 virtualization, developed by Oracle Corporation
- Vagrant: an open-source software product for building and maintaining portable virtual software development environments; e.g., for VirtualBox
- kubectl: The Kubernetes command-line tool, which allows you to run commands against Kubernetes clusters.

For MacOS, Homebrew Package Manager is a great way to install these packages with little complication, all from the command line.

[Install Homebrew on Mac](https://brew.sh/)

Once you have Homebrew installed, getting Virtualbox, Vagrant, and kubectl installed becomes very simple:

### Install Virtualbox, Vagrant, and kubectl for MacOS

Install VirtualBox:

```sh
$ brew cask install virtualbox
```

Install Vagrant:

```sh
$ brew cask install vagrant
```

install kubectl:

```sh
$ brew install kubernetes-cli
```

### Deploy your local Kubernetes cluster with Virtualbox and Vagrant

Finally, this blog post describes instructions for spinning up and connecting to a 3-node Kubernetes cluster on your local machine, using a pre-written VagrantFile:

[Kubernetes the Easy Way with k3s!](http://devnetstack.com/kubernetes-the-easy-way-with-k3s/) by [Michael Saenz](https://github.com/michaelc0n)

## Set up k3s on Raspberry Pi:

[Alex Ellis](https://www.alexellis.io/), a Cloud Architect and Consultant, has put together a buy list and instructions for deploying k3s on a Raspberry Pi cluster. Those instructions can be found [here](https://blog.alexellis.io/test-drive-k3s-on-raspberry-pi/). One thing to keep in mind here is that Raspberry Pi uses the [ARM CPU architecture](https://en.wikipedia.org/wiki/ARM_architecture), which will likely limit the container images that you can deploy.

## Set up k3s on Atomic Pi:
[Dan Garfield](https://github.com/todaywasawesome), CTO at CodeFresh, has documented a way to get the benefits of a local cluster with k3s that is accessible from an external machine, but with an [x86 architecture](https://en.wikipedia.org/wiki/X86). This requires the use of the [Atomic Pi](https://www.amazon.com/Atomic-Pi-High-Speed-Peripheral/dp/B07N298F2B). The writeup for running k3s on an Atomic Pi cluster can be found [here](https://github.com/todaywasawesome/atomic-cluster).


<!-- - [Linux Networking Explained](https://events.static.linuxfound.org/sites/events/files/slides/2016%20-%20Linux%20Networking%20explained_0.pdf) by [tgraf](https://github.com/tgraf)
- [An In-Depth Guide to iptables, the Linux Firewall](https://www.booleanworld.com/depth-guide-iptables-linux-firewall/) by [supriyo-biswas](https://github.com/supriyo-biswas)
- Monitoring and Tuning the Linux Networking Stack:
  - [Receiving Data](https://blog.packagecloud.io/eng/2016/06/22/monitoring-tuning-linux-networking-stack-receiving-data/)
  - [Sending Data](https://blog.packagecloud.io/eng/2017/02/06/monitoring-tuning-linux-networking-stack-sending-data/)

### Linux Namespaces
- [Introducing Linux Network Namespaces](https://blog.scottlowe.org/2013/09/04/introducing-linux-network-namespaces/) by [scottslowe](https://github.com/scottslowe)
- [Making sense Of Linux namespaces](https://prefetch.net/blog/2018/02/22/making-sense-of-linux-namespaces/) by [Matty9191](https://github.com/Matty9191)
- [A deep dive into Linux namespaces](http://ifeanyi.co/posts/linux-namespaces-part-1/) by [iffyio](https://github.com/iffyio)
- [Namespaces in operation](https://lwn.net/Articles/531114/) by [mkerrisk](https://github.com/mkerrisk)
- [Containers from Scratch](https://speakerdeck.com/ericchiang/coreos-fest-2017-containers-from-scratch), [recording](https://www.youtube.com/watch?v=wyqoi52k5jM) by [ericchiang](https://github.com/ericchiang)
- Containers from scratch: The sequel, [recording](https://www.youtube.com/watch?v=_TsSmSu57Zo) by [lizrice](https://github.com/lizrice)
- [Linux Namespaces](https://medium.com/@teddyking/linux-namespaces-850489d3ccf) by [teddyking](https://github.com/teddyking)
- [Namespaces, Threads, and Go](https://github.com/containernetworking/plugins/tree/master/pkg/ns) by [squeed](https://github.com/squeed)
  - [Linux Namespaces and Go Don't Mix](https://www.weave.works/blog/linux-namespaces-and-go-don-t-mix) by [brb](https://github.com/brb)

## Kubernetes Networking
- [The Almighty Pause Container](https://www.ianlewis.org/en/almighty-pause-container) by [ianlewis](https://github.com/ianlewis)
- There is No Such Thing as Container Networking, [recording](https://www.youtube.com/watch?v=t98CX8Tberc) by [kelseyhightower](https://github.com/kelseyhightower)
- [Kubernetes Networking: Behind the scenes](https://medium.com/@nleiva/kubernetes-networking-behind-the-scenes-39a1ab1792bb) by [nleiva](https://github.com/nleiva)
- [Kubernetes Networking Demystified: A Brief Guide](https://www.cncf.io/blog/2020/01/30/kubernetes-networking-demystified-a-brief-guide/)
- [Understanding kubernetes networking: pods](https://medium.com/google-cloud/understanding-kubernetes-networking-pods-7117dd28727) by [Markbnj](https://github.com/Markbnj)
- [An illustrated guide to Kubernetes Networking [Part 1]](https://medium.com/@ApsOps/an-illustrated-guide-to-kubernetes-networking-part-1-d1ede3322727) by [ApsOps](https://github.com/ApsOps)
- [A Hacker’s Guide to Kubernetes Networking](https://thenewstack.io/hackers-guide-kubernetes-networking/) by [yaronha](https://github.com/yaronha)
- [Kubernetes Cluster Networking](https://kubernetes.io/docs/concepts/cluster-administration/networking/)
- [Why Kubernetes doesn’t use libnetwork](https://kubernetes.io/blog/2016/01/why-kubernetes-doesnt-use-libnetwork/) by [thockin](https://github.com/thockin)
- [Understanding kubernetes networking: services](https://medium.com/google-cloud/understanding-kubernetes-networking-services-f0cb48e4cc82) by [Markbnj](https://github.com/Markbnj)
- [Kubernetes Networking](https://cloudnativelabs.github.io/post/2017-04-18-kubernetes-networking/) by [cloudnativelabs](https://github.com/cloudnativelabs)
- [Understand and Troubleshoot the “Magic” of k8s Networking](https://kccnceu18.sched.com/event/Dquy/blackholes-and-wormholes-understand-and-troubleshoot-the-magic-of-kubernetes-networking-minhan-xia-rohit-ramkumar-google-intermediate-skill-level-slides-attached), [recording](https://www.youtube.com/watch?v=knIJEzTd3kc) by [rramkumar1](https://github.com/rramkumar1) and [freehan](https://github.com/freehan)
- [An Illustrated Guide to Kubernetes Networking](https://speakerd.s3.amazonaws.com/presentations/005d36f0113d4773be8866496142485e/Illustrated_guid_to_kubernetes_networking.pdf) by [thockin](https://github.com/thockin)
- [The ins and outs of networking in Google Container Engine and Kubernetes](https://speakerdeck.com/thockin/the-ins-and-outs-of-networking-in-google-container-engine), [recording](https://www.youtube.com/watch?v=y2bhV81MfKQ) by [thockin](https://github.com/thockin) and [matchstick](https://github.com/matchstick)
- Introduction to Kubernetes Networking, [recording](https://www.youtube.com/watch?v=7OFw3lgSb1Q) by [bboreham](https://github.com/bboreham)
- [Life of a Packet](https://github.com/sbueringer/kubecon-slides/blob/master/slides/2017-kubecon-eu/Life%20of%20a%20Packet%20%5BI%5D%20-%20Michael%20Rubin%2C%20Google%20-%20KubeCon%20EU%20'17-%20Life%20of%20a%20Packet.pdf), [recording](https://www.youtube.com/watch?v=0Omvgd7Hg1I) by [matchstick](https://github.com/matchstick)
- [Google Kubernetes Engine networking](https://cloud.google.com/kubernetes-engine/docs/concepts/network-overview)
- [Operating a Kubernetes network](https://jvns.ca/blog/2017/10/10/operating-a-kubernetes-network/) by [jvns](https://github.com/jvns)
- [Understanding the Kubernetes Networking Model](https://sookocheff.com/post/kubernetes/understanding-kubernetes-networking-model/) by [soofaloofa](https://github.com/soofaloofa)
- [Kubernetes Networking Master Class](https://rancher.com/events/2018/kubernetes-networking-masterclass-june-online-meetup/)
- [Kubernetes and Networks - why is this so dang hard?](https://speakerdeck.com/thockin/kubernetes-and-networks-why-is-this-so-dang-hard) by [thockin](https://github.com/thockin)
- [Bringing Traffic Into Your Kubernetes Cluster](https://speakerdeck.com/thockin/bringing-traffic-into-your-kubernetes-cluster) by [thockin](https://github.com/thockin)
- [Deconstructing Kubernetes Networking](https://eevans.co/blog/deconstructing-kubernetes-networking/)

### IPVS
- [IPVS-Based In-Cluster Load Balancing Deep Dive](https://kubernetes.io/blog/2018/07/09/ipvs-based-in-cluster-load-balancing-deep-dive/)

### eBPF
- [eBPF, Microservices, Docker, and Cilium: From Novice to Seasoned](http://www.adelzaalouk.me/2017/security-bpf-docker-cillium/) by [zanetworker](https://github.com/zanetworker)
- [Why is the kernel community replacing iptables with BPF?](https://cilium.io/blog/2018/04/17/why-is-the-kernel-community-replacing-iptables/) by [cilium](https://github.com/cilium)
- [Using eBPF in Kubernetes](https://kubernetes.io/blog/2017/12/using-ebpf-in-kubernetes/)
- [BPF and XDP Reference Guide](https://cilium.readthedocs.io/en/v1.1/bpf/) by [cilium](https://github.com/cilium)

### IPv6
- [IPv4/IPv6 dual-stack](https://kubernetes.io/docs/concepts/services-networking/dual-stack/)
- [Dual-stack Kubernetes with kubeadm-dind-cluster](http://blog.michali.net/2018/11/08/dual-stack-kubernetes-with-kubeadm-dind-cluster/) by [pmichali](https://github.com/pmichali)
- [kube-v6](https://github.com/leblancd/kube-v6) by [leblancd](https://github.com/leblancd)
- [Kubernetes in IPv6 only](https://opsnotice.xyz/kubernetes-ipv6-only/) by [valentin2105](https://github.com/valentin2105)
- [Add IPv4/IPv6 dual stack KEP](https://github.com/kubernetes/enhancements/pull/648)

### Multi-cluster
- [Kubernetes multi-cluster networking made simple](https://medium.com/@nleiva/kubernetes-multi-cluster-networking-made-simple-c8f26827813) by [nleiva](https://github.com/nleiva)

## CNI
- [Container Network Interface Specification](https://github.com/containernetworking/cni/blob/master/SPEC.md)
- [Container Network Interface and Go](https://www.youtube.com/watch?v=0SXPsLvB0UI)
- [Understanding CNI (Container Networking Interface)](https://www.dasblinkenlichten.com/understanding-cni-container-networking-interface/)
- CNI, the Container Network Interface, [recording](https://skillsmatter.com/skillscasts/10811-cni-the-container-network-interface) by [bboreham](https://github.com/bboreham)
- The Container Network Interface (CNI), [recording](https://www.youtube.com/watch?v=_-9kItVUUCw) by [eyakubovich](https://github.com/eyakubovich)
- KubeCon "Container Network Interface: Network Plugins", [recording](https://www.youtube.com/watch?v=-DB1nxrUwbA) by [eyakubovich](https://github.com/eyakubovich)
- [Kubernetes and the CNI Where We Are and What's Next](https://github.com/sbueringer/kubecon-slides/blob/master/slides/2018-kubecon-eu/Kubernetes%20and%20the%20CNI%20Where%20We%20Are%20and%20What's%20Next%20-%20Casey%20Callendrello%2C%20CoreOS%20(Intermediate%20Skill%20Level)%20-%20Kubernetes-and-the-CNI-Kubecon-218.pdf), [recording](https://www.youtube.com/watch?v=Vn6KYkNevBQ) by [squeed](https://github.com/squeed)
- [Comparative Kubernetes networks solutions](https://www.objectif-libre.com/en/blog/2018/07/05/k8s-network-solutions-comparison/)
- [Comparison of Networking Solutions for Kubernetes](http://machinezone.github.io/research/networking-solutions-for-kubernetes/)
- [Comparative Kubernetes networks solutions](https://www.objectif-libre.com/en/blog/2018/07/05/k8s-network-solutions-comparison/)
- [Benchmark results of Kubernetes network plugins (CNI) over 10Gbit/s network](https://itnext.io/benchmark-results-of-kubernetes-network-plugins-cni-over-10gbit-s-network-36475925a560)
- [Large-scale network simulations in Kubernetes, Part 1 - Building a CNI plugin](https://networkop.co.uk/post/2018-11-k8s-topo-p1/)
- [Large-scale network simulations in Kubernetes, Part 2 - Network topology](https://networkop.co.uk/post/2018-11-k8s-topo-p2/)
- [How to Write Your Own CNI Plug-in with Bash](https://www.altoros.com/blog/kubernetes-networking-writing-your-own-simple-cni-plug-in-with-bash/)

## Network Solutions Details

### Calico
- [Calico for Kubernetes networking: the basics & examples](https://medium.com/flant-com/calico-for-kubernetes-networking-792b41e19d69)


## DNS
- [An Introduction to the Kubernetes DNS Service](https://www.digitalocean.com/community/tutorials/an-introduction-to-the-kubernetes-dns-service)
- [5 – 15s DNS lookups on Kubernetes?](https://blog.quentin-machu.fr/2018/06/24/5-15s-dns-lookups-on-kubernetes/) by [Quentin-M](https://github.com/Quentin-M)
- [Debugging and Monitoring DNS issues in Kubernetes](https://cilium.io/blog/2019/12/18/how-to-debug-dns-issues-in-k8s/)

## Routing
- [Kubernetes Traffic Engineering with BGP](https://www.asykim.com/blog/kubernetes-traffic-engineering-with-bgp) by [andrewsykim](https://github.com/andrewsykim)

## Service Mesh

- The Service Mesh: Past, Present, and Future, [recording](https://www.youtube.com/watch?v=2trOvMUuLkk) by [wmorgan](https://github.com/wmorgan)
- [Using Istio Multicluster to "Burst" Workloads Between Clusters](https://codelabs.developers.google.com/codelabs/istio-multi-burst/#0) -->
