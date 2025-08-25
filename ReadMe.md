# RMIT User-Guide

## SRSRan Setup
1. Create Ue-namespaces and network gateways
```bash
cd /home/ubuntu/ashish_work_dir/scripts
./intial_network_routing.sh
```

2. Start Open5gs Core
```bash
cd /home/ubuntu/ashish_work_dir/scripts
./run_core
```

3. Start N Gnbs
```bash
# To start a single gnb, use ./run_gnb.sh <GNB_ID>
./run_gnb.sh 5
# The above command will start single gnb with pci-id = 5
```
