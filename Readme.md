This reposiory contains about two files one is master script and the other is node/worker script which helps in setting up the Kubernetes architecture through "kubectl"

Please follow the instructions as stated in this script 

How to setup architecture with this two scripts ?

Ans: Take two three EC2 instances in any Cloud Provider or on local V.M., In that one will be the master node and other two will be master nodes...

Master Node(ec2) : t2/t3.medium
worker(ec2) : t2.medium

Just launch these two instances in any region you wanted but make sure you launch in the subnet for no further problems

Log in Master node :
 switch to root user : sudo su -
 paste the master script given here by naming as <file.sh>( cat master.sh --> paste it, write and quit --)
 run the script (sh script.sh)

 Wait for some time you will be seeing the script executing the tasks and at the end of script you will be seeing
 something "Cluster Joining Command and under it there will be one line with "kubeadm join 172.31.11.67:6443 --token e7e6eq.5dvrwzr35yd8rfi9 --discovery-token-ca-cert-hash sha256:" 
Make sure to copy this command this will be helpful in setting the slave node

Now Launch the slave node 1:
  switch to root user : sudo su -
  Now paste the node script by creating a file <node.sh> ( cat node.sh --> paste it, write and quit --)
  In the script you will see a line which contains MASTER_JOIN_COMMAND="" , now enter the Output which we received in the master script( kubeadm join ..)
  Save and run the script 
  Wait for some time and you are done..

Now go to master machine and give command "kubectl get nodes -A" you should see your two workers nodes listed/
