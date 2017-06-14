# Try prometheus
Provides a simple vagrant box to install and run sample Prometheus instance as written on prometheus.io

```
git clone https://github.com/antontsv/try-prometheus && \
cd try-prometheus && \
vagrant plugin install vagrant-cachier && \
vagrant up
```

To see results, open 
* http://10.100.100.121:9090 for UI 
* http://10.100.100.121:9090/metrics to see self-produced metrics