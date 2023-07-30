<h1>Troubleshooting AWS Network Connectivity Security Groups and NACLs</h1>


<h2>Description</h2>
Troubleshooting basic network connectivity issues is an important skill. This troubleshooting scenario is an opportunity to assess your skills in this area.

In this lab scenario, a junior administrator has deployed a VPC and instances, but there are a few things wrong. Instance3 is not able to connect to the internet and the junior admin can't determine why. Being a senior administrator, it's your responsibility to troubleshoot the issue and ensure the instance has connectivity to the internet, so that you can ping and log in to the instance using SSH.

<br />

<h2>Environments Used </h2>

- <b>Windows 11</b>
- <b>AWS</b>
- <b>Linux</b>
  
<h2>Program walk-through:</h2>

1. Navigate to the EC2 dashboard.
2. Click Instances (running).
3. Select Instance3 from the list and review the instance details. (NOTE: Notice Instance3 does not have a public IP address.)
4. At the top of the page, click Actions, to select Networking, and select Manage IP addresses.
5. In the tooltip box, click allocate to be redirected to the Elastic IP addresses list.
6. In the top-right corner, click Allocate Elastic IP address.
7. Leave the settings as default and click Allocate.
 <br/>
 
<p align="center">
<img src="https://i.imgur.com/wlwMIgu.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Select the IP address and click the Actions dropdown menu to select Associate Elastic IP address. <br/>
For Instance, select Instance3 and click Associate.

 <br/>
 
<p align="center">
<img src="https://i.imgur.com/01h1ERs.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Copy the public IP address of Instance 3 and attempt to ping the instance from either your own local terminal or ssh into Instance 1 to do the ping test

 <br/>
 
<p align="center">
<img src="https://i.imgur.com/XVZCHw2.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

1. Navigate back to AWS Instances page.
2. Select Instance3 from the list of instances.
3. Click Security tab to review the associated security group.
4. Review the security group details.
5. In the left-hand menu, click Security Groups.
6. Scroll to Security group name and expand the field to locate EC2SecurityGroup3.
7. Click Inbound rules tab to view the allow and deny inbound rules.
8. Click Outbound rules tab to view the allow and deny outbound rules.


 <br/>
 
<p align="center">
<img src="https://i.imgur.com/oJrXVro.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
<img src="https://i.imgur.com/OYcmOFm.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

1. In the left-hand menu, click Instances.
2. Select Instance3 and click Networking tab to view the private subnet IP address.
3. In a new tab, navigate to VPC.
4. In the left-hand menu, click Subnets to find the private subnet IP address that matches Instance3.
5. Select PublicSubnet4 and click Network ACL tab.
6. Click on the link next to Network ACL.
7. Click Inbound rules tab to view the allow and deny inbound rules.
8. Click Outbound rules tab to view the allow and deny outbound rules.

 <br/>
 
<p align="center">
<img src="https://i.imgur.com/8JE03tC.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

1. Select Public3-NACL.
2. Click Inbound rules tab to view the allow and deny inbound rules.
3. Click Outbound rules tab to view the allow and deny outbound rules.


 <br/>
 
<p align="center">
<img src="https://i.imgur.com/iUeEp51.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
<img src="https://i.imgur.com/cffmZ9g.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

1. In the left-hand menu, click Subnets and select PublicSubnet4.
2. Click Network ACL tab and click Edit network ACL association.
3. For Network ACL ID, select Public3-NACL from the dropdown menu.
4. Click Save.

 <br/>
 
<p align="center">
<img src="https://i.imgur.com/vb7jYMC.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Navigate back to the terminal to verify ping results. It should still fail.

 <br/>
 
<p align="center">
<img src="https://i.imgur.com/CX0VUlI.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

1. Navigate back to the AWS Subnets page and click Route table tab to view the associated route table, Private3-RT.
2. Click Edit route table association.
3. For Route table ID, select Public3-RT from the dropdown menu.
4. Click Save.


 <br/>
 
<p align="center">
<img src="https://i.imgur.com/DpasP7d.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />

Navigate back to the terminal to confirm successful ping results. It should ping this time.


 <br/>
 
<p align="center">
<img src="https://i.imgur.com/INTre5A.png" height="80%" width="80%" alt="Disk Sanitization Step"/>
</p>

<br />
<br />
