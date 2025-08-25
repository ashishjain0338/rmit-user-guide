# RMIT User-Guide

## SRSRan Setup
1. Create Ue-namespaces and network gateways
```bash
cd /home/ubuntu/ashish_work_dir/scripts
./intial_network_routing.sh
```
2. Restart Kafka Services
```bash
sudo systemctl daemon-reload
sudo systemctl start zookeeper
sudo systemctl start kafka
sudo systemctl status zookeeper
sudo systemctl status kafka
```

3. Start Open5gs Core
```bash
cd /home/ubuntu/ashish_work_dir/scripts
./run_core
```

4. Start N Gnbs
  To start a single gnb, use `./run_gnb.sh <GNB_PCI_ID>`
  ```bash
  ./run_gnb.sh 5
  # The above command will start single gnb with pci-id = 5
  ```
  To start all gnbs together, use `./run_all_gnbs.sh`
  ```bash
  ./run_all_gnbs.sh
  ```
  Note: You can change the number of gnbs by modifying the variable `NUM_GNBS` in the script. The logs will be found under the folder `gnb-logs`

5. Connect N Ue's
   To start a single ue, use `./run_ue.sh <ue_id>`
  ```bash
  ./run_ue.sh 5
  # The above command will start ue which will try to connect to gnb with pci-id = 5
  ```
To start all ues together, use `./run_all_ues.sh`
  ```bash
  ./run_all_ues.sh
  ```
  Note: You can change the number of ues by modifying the variable `NUM_GNBS` in the script. The logs will be found under the folder `ue-logs`

6. Confirm PDU establishment
```bash
python3 analyse_ue_logs.py
```

7. Start Traffic Generation Script
```bash
cd /home/ubuntu/ashish_work_dir/scripts/traffic-generation/multi_ue_generation_script
./generate-multi-cell-traffic.sh
```
Note: The logs will be stored under the folder `traffic-logs`

8. Retrieve Data from Kafka Topic
```bash
/usr/local/kafka/bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic testTopic --from-beginning
```
Note: The kafka message will contains 5 comma separated-values as per the schema: `PCI_ID, dlprb_usage, ulprb_usage, dl_brate, ul_brate, sinr`

