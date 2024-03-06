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
<img src="..." height="30%" width="70%" alt="Disk Sanitization Steps"/>
