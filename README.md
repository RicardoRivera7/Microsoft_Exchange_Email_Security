<h1>Microsoft Exchnage Email Security</h1>


<h2>Description</h2>
Step-by-step process utilizing microsoft exchange to create mail flow rules to block suspicious emails, links and attachments
<br />

<h2>Prerequisites</h2>
- <b>Make a Microsoft Azure Account: https://azure.microsoft.com/en-us/pricing/purchase-options/azure-account <br/> 
- Microsoft 365 Business Premium trial (get 1st or you can't get the next trial) <br/> 
- <b>Microsoft Defender for Office 365 (plan 1) trial (get 2nd)</b> <br/>

<h2>Software Used</h2>

- <b>Microsoft Azure (using free subscription) </b> 

<h2>Environments Used </h2>

- <b>Microsoft Azure</b>
- <b>Microsoft Exchange</b>
- <b>Microsoft 365 Admin</b>

<h2>Links</h2>

-[Azure Free Subscription](https://azure.microsoft.com/en-us/pricing/purchase-options/azure-account)
<br/>
-[Azure Virtual Machines](https://portal.azure.com)
<br/>
<br/>
<br/>



<p align="left">

<h2>Creating a Resource Group</h2>

Go to the Azure portal at the homepage and click on "Resource Groups" <br/>
Click "Create" <br/>
If you're using a Free account then the Subscription section will be something like "Azure Subscription 1", it should already be selected for you <br/>
For "Resource Group Name", name it whatever you like, I named mine "SOCLab" <br/>
For "Region" select something near you or that is in a reasonable distance that wont cause connection issues, and keep in mind which one you choose as we'll need this in the future too <br/>
<img src="https://i.imgur.com/oKKF1z5.png" height="80%" width="80%" alt="AzureCloudSOC"/>
<br/>
<br/>

Click the blue "Review + Create" button <br/>
Then click the blue "Create" button <br/>
Refresh the page and you should see your resource group there! <br/>
<em>Note: don't mind the other resource groups you see in my screenshot, those were just for fun, you will only have the one you made</em> <br/>
<img src="https://i.imgur.com/78dmS0D.png" height="80%" width="80%" alt="AzureCloudSOC"/>
<br/>
<br/>

<h2>Creating a Vritual Network</h2>

Now we need to create a virtual network for our VM to connect to once its made <br/>
Navigate back to the home page and click on "Virtual Networks" <br/>
Do the Following: <br/>
<em>For "Subscription", make sure it is set to your correct one, in my case its "Azure Subscription 1" <br/>
For "Resource Group", select the one you made in the previous section, for me it was "SOCLab" <br/>
For "Virtual Network Name", make it any name you want <br/>
For "Region", select the same one you used to make the resource group, mine was US West 2 <br/> </em>
<img src="https://i.imgur.com/IgnjHtg.png" height="80%" width="80%" alt="AzureCloudSOC"/>
<br/>
<br/>

Click the blue "Review + Create" button <br/>
Then click the blue "Create" button <br/>
You should get a deployment page and confirmation it has been deployed, this could take a minute <br/>
<img src="https://i.imgur.com/Uo4W8dc.png" height="80%" width="80%" alt="AzureCloudSOC"/>
<br/>
<br/>

<h2>Creating a Virtual Machine</h2>

It's time to create the virtual machine! <br/>
Navigate back to the home page and click on "Virtual Machines" <br/>
Click "Create" and select the "Virtual Machine" option <br/>
<img src="https://i.imgur.com/5rpizrH.png" height="80%" width="80%" alt="AzureCloudSOC"/>
<br/>
<br/>

Do the Following:
<em>For "Resource Group", select the one you made <br/>
For "Virtual Machine Name", name it whatever you want, I did BlueTeamMachine <br/>
For "Region", select the same one you've been using so far <br/>
For "Zone Options", you can select "Azure-Selected Zone" to let it autopick for you, otherwise you can do "Self-Selected" zone to pick yourself <br/>
You can leave "Security Type" on "Trusted launch Virtual machines" <br/>
<img src="https://i.imgur.com/gft0rYA.png" height="80%" width="80%" alt="AzureCloudSOC"/>
<br/>
<br/>

For "Image" im picking windows 10, to do this click on the dropdown next to image and scroll all the way down to click on "See all images" <br/>
Search for "Windows 10" if you don't see it on the front page <br/>
Select it and choose any of the Gen 2 images <br/>
<img src="https://i.imgur.com/KidmTj7.png" height="80%" width="80%" alt="AzureCloudSOC"/>
<br/>
<br/>

For "Username" and "Password" you can set those to whatever you want <br/>
Make sure "Public Inbound Ports" has the "Allowed Selected Ports" option chosen <br/>
Make sure "Select Inbound Ports" has RDP (Remote Desktop Protocol) 3389 on <br/>
Under "Licensing" check the box </em><br/>
<img src="https://i.imgur.com/3g1yKSm.png" height="80%" width="80%" alt="AzureCloudSOC"/>
<br/>
<br/>

Click "Next" until you get to the "Networking section" <br/>
Find the checkbox for "Delete public IP and NIC when VM is deleted" and check it, this will make sure your VM and anything associated with it is completley wiped if you delete it <br/>

<img src="https://i.imgur.com/3g1yKSm.png" height="80%" width="80%" alt="AzureCloudSOC"/>
<br/>
<br/>

Click the blue "Review + Create" button <br/>
Then click the blue "Create" button <br/>
You should get a deployment page and confirmation it has been deployed, this could take a minute <br/>
<img src="https://i.imgur.com/m78nNGU.png" height="80%" width="80%" alt="AzureCloudSOC"/>
<br/>
<br/>

<h2>Creating and Configuring Log Analytics Workspace</h2>

Navigate back to the home page <br/>
Under "Azure Services", click on the arrow that says "More Services" <br/>
In the search bar type in "Log" and select "Log Analytics Workspaces" <br/>
<img src="https://i.imgur.com/yTUhEM6.png" height="80%" width="80%" alt="AzureCloudSOC"/>
<br/>
<br/>
