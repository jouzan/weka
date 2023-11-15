# weka
Weka related scrips 

# Install Linux OS pre req
## ================================


1. setup statis IP
2. Setup MTU 9001
3. Setup network-scripts
4. disable network manager
5. Install software tools
6. Download weka
7. Install weka 

# curl http://192.168.44.234:14000/dist/v1/install | sh
# weka version get --set-current 4.2.5 --from 192.168.44.234:14000
# weka local start


9. weka local ps
10. weka status
11. weka version
    
12. configure / create cluster
weka cluster create weka1 weka2 weka3 weka4 weka5 --host-ips=192.168.44.234,192.168.37.176,192.168.36.189,192.168.32.189,192.168.45.209
