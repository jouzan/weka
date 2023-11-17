# weka
Weka related scrips 

# Install Linux OS pre req
## ================================


1. Make sure space on OS drie is 500GB min
2. setup statis IP
3. Setup MTU 9001
4. Setup network-scripts
5. disable network manager
6. Install software tools

# Download weka and install it on one server 
## =========================================================================
6. Download weka
   wget --auth-no-challenge https://4kl036ikhstPZQ8P:@get.weka.io/dist/v1/pkg/weka-4.2.5.tar
8. Install weka
   tar -xvf weka-4.2.5.tar
   cd /weka
   ./install.sh 

# Download weka and install it on other server from the first server  
## ========================================================================
1.  curl http://192.168.44.234:14000/dist/v1/install | sh
2.  weka version get --set-current 4.2.5 --from 192.168.44.234:14000
3.  weka local start


4.  eka local ps
5.  weka status
6. . weka version

# Confiure cluster 
## ========================================================================
weka cluster create weka1 weka2 weka3 weka4 weka5 --host-ips=192.168.44.234,192.168.37.176,192.168.36.189,192.168.32.189,192.168.45.209

you can now use browser to loginto the portal http://192.168.44.234:14000   admin  admin    

weka cluster update --cluster-name WEKADEV 

weka clous enable 

weka cloud status 

weka cluster containers dedicate 0 on        [do that for all hosts ] 
for i in {0..4} ; do weka cluster container dedicate $i on ; done

for i in {0..5} ; do weka cluster container net add $i eth0 --gateway 192.168.31.1 --netmask 20 ; done 

for i in {0..5} ; do weka cluster container cores $i 19 --frontend-dedicated-cores 1 --drives-dedicated-cores 6 ; done  

for i in {0..5} ; do weka cluster container drive add $i /dev/sdb /dev/sdc /dev/sdd /dev/sde /dev/sdf /dev/sdh ; done  

# Confiure protection parity and spare  
## ========================================================================

weka cluster update --data-drives 4 --parity-drives 2 

weka cluster hotspare 1 


# Verify 
## ========================================================================

weka cluster drive 
weka cluster container resources 0 
weka status 

weka cluster container apply --all --force        [now the status will be ready   ] 


# Verify 
## ========================================================================
weka cluster start-io     
weka status     [you will see drives are up,  capacity   , cloud connection  ,  see alerts on system  , the licnese ] 






