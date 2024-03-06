<h2>SOC Automation Lab Part 3</h2>

<h3>Objectives</h3>
- Configure TheHive & Wazuh Server  
<br />
<br />

To start, I open Cassandra's configuration file using the command "nano /etc/cassandra/cassandra.yaml" and proceed to edit the listen address, RPC address, and the seed provider address to reflect TheHive's public IP address.
<br />
<img src="https://github.com/Yagoobz/SOCAutomationLabPart3/assets/145611184/951d944f-7035-4fdd-a95b-e4971947f27c" height="30%" width="70%" alt="Disk Sanitization Steps"/>

Following the configuration changes in Cassandra, I halt the Cassandra service using the command "systemctl stop cassandra.service." Since I installed TheHive using their package, I need to remove the old files, which I achieve with "rm -rf /var/lib/cassandra/*." With that completed, I restart Cassandra by executing "systemctl start cassandra.service." To ensure everything is running smoothly, I like to verify the status of the services, which can be done with "systemctl status ..." command.
<br />
<img src="https://github.com/Yagoobz/SOCAutomationLabPart3/assets/145611184/fbfd87aa-2525-4bff-842b-27455a86cc9c" height="30%" width="70%" alt="Disk Sanitization Steps"/>

To set up Elasticsearch, which manages data indices, I navigate to the configuration files using "nano /etc/elasticsearch/elasticsearch.yml." Within the configuration, I remove the comment for the cluster name and change it to "the hive," uncomment the node name, uncomment the network host and input TheHive's public IP address, and uncomment the cluster initial master nodes, removing node 2 since I don't have a second node. Then, I start the Elasticsearch service with "systemctl start ...," and enable it using "systemctl enable ...". Finally, I verify if the service is up and running, and indeed it is. We're good to go!
<br />
<img src="..." height="30%" width="70%" alt="Disk Sanitization Steps"/>
