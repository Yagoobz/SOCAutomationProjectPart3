<h2>SOC Automation Project Part 3</h2>

<h3>Objectives</h3>
- Configure TheHive & Wazuh Server  
<br />
<br />

To start, I open Cassandra's configuration file using the command "nano /etc/cassandra/cassandra.yaml" and proceed to edit the listen address, RPC address, and the seed provider address to reflect TheHive's public IP address.
<br />
<br />
<img src="https://github.com/Yagoobz/SOCAutomationLabPart3/assets/145611184/951d944f-7035-4fdd-a95b-e4971947f27c" height="30%" width="70%" alt="Disk Sanitization Steps"/>

Following the configuration changes in Cassandra, I halt the Cassandra service using the command "systemctl stop cassandra.service." Since I installed TheHive using their package, I need to remove the old files, which I achieve with "rm -rf /var/lib/cassandra/*." With that completed, I restart Cassandra by executing "systemctl start cassandra.service." To ensure everything is running smoothly, I like to verify the status of the services, which can be done with "systemctl status ..." command.
<br />
<br />
<img src="https://github.com/Yagoobz/SOCAutomationLabPart3/assets/145611184/fbfd87aa-2525-4bff-842b-27455a86cc9c" height="30%" width="70%" alt="Disk Sanitization Steps"/>

To set up Elasticsearch, which manages data indices, I navigate to the configuration files using "nano /etc/elasticsearch/elasticsearch.yml." Within the configuration, I remove the comment for the cluster name and change it to "the hive," uncomment the node name, uncomment the network host and input TheHive's public IP address, and uncomment the cluster initial master nodes, removing node 2 since I don't have a second node. Then, I start the Elasticsearch service with "systemctl start ...," and enable it using "systemctl enable ...". Finally, I verify if the service is up and running, and indeed it is. We're good to go!
<br />
<br />
<img src="https://github.com/Yagoobz/SOCAutomationLabPart3/assets/145611184/1d9ec576-fba9-4047-a5b7-94915dfa1300" height="30%" width="70%" alt="Disk Sanitization Steps"/>

To ensure that TheHive's user and group have access to a specific file path, I execute the command "ls -la /opt/thp." This verifies the permissions of the directory that TheHive requires access to. If I find that the root has access to TheHive directory, I need to change that by running "chown -R thehive:thehive /opt/thp." Upon rechecking the permissions using "ls -la /opt/thp," I confirm that TheHive is now both the user and the group with access. Now, I'm ready to proceed with configuring TheHive's configuration file.
<br />
<br />
<img src="https://github.com/Yagoobz/SOCAutomationLabPart3/assets/145611184/d4ebc5da-e67a-4736-b068-1795d5e676b4" height="30%" width="70%" alt="Disk Sanitization Steps"/>

After accessing the configuration file at "/etc/thehive/application.conf" with "nano /etc/thehive/application.conf," I update the storage hostname and index search hostname to TheHive's IP address, followed by modifying the application's local host to TheHive's IP address. With these changes made, I proceed to start and enable TheHive using "systemctl start ..." and verify the service's status for confirmation.
<br />
<br />
<img src="https://github.com/Yagoobz/SOCAutomationLabPart3/assets/145611184/7bb106ac-098e-45a9-8162-93f9bf385685" height="30%" width="70%" alt="Disk Sanitization Steps"/>

With all three services - Cassandra, Elasticsearch, and TheHive - up and running, I attempt to access TheHive using its public IP address followed by port 9000. Upon entering the default username and password, I successfully gain access to TheHive. Mission accomplished!
<br />
<br />
<img src="https://github.com/Yagoobz/SOCAutomationLabPart3/assets/145611184/795ec3ab-c3f9-4a83-989f-8e7602bf8e19" height="30%" width="70%" alt="Disk Sanitization Steps"/>

When I returned to my Windows cloud machine, I encountered an issue accessing the Wazuh dashboard due to a peculiar cloud server setting. To work around this, I opted to create a new Windows 10 virtual machine on VMware, running on an older MacBook with an Intel chip, as it does not face the compatibility challenges of Apple's M Series chips with virtual machines. After reinstalling Sysmon, everything was operational again, and VMware proved to run more smoothly compared to the AWS server. With access restored, I logged into the Wazuh dashboard and proceeded to create a new agent. Upon creation, I received a command to download in Windows PowerShell, and to initiate the service, I executed "net start wazuhsvc." Verifying in the services, Wazuh was indeed running as expected.
<br />
<br />
<img src="https://github.com/Yagoobz/SOCAutomationLabPart3/assets/145611184/69e45ab9-01a4-41b0-8d3f-b4b803f700a3" height="30%" width="70%" alt="Disk Sanitization Steps"/>
