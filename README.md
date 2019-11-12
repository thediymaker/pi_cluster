       .~~.   .~~.
      '. \ ' ' / .'
       .~ .~~~..~.                       _                          _
      : .~.'~'.~. :      ___ ___ ___ ___| |_ ___ ___ ___ _ _    ___|_|
     ~ (   ) (   ) ~    |  _| .'|_ -| . | . | -_|  _|  _| | |  | . | |
    ( : '~'.~.'~' : )   |_| |__,|___|  _|___|___|_| |_| |_  |  |  _|_|
     ~ .~ (   ) ~. ~                |_|                 |___|  |_|
      (  : '~' :  )      ___ _   _ _ ___ _____ ___ ___
       '~ .~~~. ~'      | __| |_| | |_ -|_   _| -_| -_|
           '~'          |___|___|___|___| |_| |___|_|_|

This initial setup is for an 8 node cluster, 1 login node with 7 compute nodes. The master is setup to nat traffic to the compute nodes as well as provide DHCP. The master node is the only one that requires connecting to the internet over the wifi.

Setting up the raspberry pi cluster

1. Flash raspbarian to the SD card on each of the pies.
2. Login with "pi" "raspberry", change the default password.
3. Enable SSH "systemctl enable ssh" "systemctl start ssh"
4. Set hostname "hostnamectl set-hostname pi_nodeXX"
5. Login in to the head node and add the hosts information to the ansible hosts file
6. Modify the pi_compute_node_setup.yml to include the hosts in the required spots
7. Modify the pi_login_node_setup.yml to include all of the correct hosts in the required spots including the required DHCP info.
8. Run "ssh-copy-id pi@pi_nodeXX" from the login node to setup passwordless ssh
9. Run the ansible pi_login_node_setup.yml playbook
10. Run the ansible pi_compute_node_setup.yml playbook
