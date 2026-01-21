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
-[Azure Portal](https://portal.azure.com)
<br/>
-[Microsoft 365 Admin Center](https://go.microsoft.com/fwlink/?linkid=2081615) 
<br/>
-[Microsoft Outlook](https://outlook.office.com/) (Use to check employee and admin emails)  
<br/>
<br/>
<br/>



<p align="left">

<h2>Creating Users and assigning Licenses</h2>

Go to the Microsoft 365 Admin center create an account if you do not have one, this will be your global admin <br/>
On the left side click on "Users" then "Active Users" <br/>
On this page you should see an option to "Add User" <br/>
Let's make an employee account first (make as many as you want), enter a display name such as employee1 or employee-john  <br/>
For the username you can copy whatever you entered in display name or mix them (Ex: For display name I did employee-jojo and for username i did employee9) <br/>
Leave the two checkboxes toggled <br/>
<img src="https://i.imgur.com/rmTBInE.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>

Click the blue "Review + Create" button <br/>
Then click the blue "Create" button <br/>
Refresh the page and you should see your resource group there! <br/>
<em>Note: don't mind the other resource groups you see in my screenshot, those were just for fun, you will only have the one you made</em> <br/>
<img src="https://i.imgur.com/78dmS0D.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>



Click "Next" <br/>
Assign the two licenses to the account (Microsoft 365 Business Premium and Microsoft Defender for Office 365 Plan 1) <br/>
Click "Next" <br/>
<img src="https://i.imgur.com/Hgax8Ep.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>


In the "Optional Settings" section make sure role is toggled as User and finish making the account <br/>
Once done go to the password, click "Show" and copy the password somewhere to save it  <br/>
Now add another user except for admin <br/>
make both the display and user name the samething <br/>
In the "Optional Settings" section, set the role to "Admin Center Access" and check the boxes for "Exchange Administrator" and "User Administrator" <br/>
<img src="https://i.imgur.com/yhosxI5.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>

Finish making the account and save the password for this one too <br/>
Congrats you now have both an admin and user account with the appropriate licenses <br/>

<h2>Creating and Managing Defender Policies</h2>

Our licenses gives us some nice options to manage in Defender such as Safe links, and phishing policies <br/>
Navigate to the defender portal and sign in with your global admin account (Not the admin account you created before, this will be the main account you made whe signing up for Azure) <br/>
On the left side click on "Email and Collaboration" and click on "Policies and rules" <br/>
Click on "Threat Policies" <br/>
We can see s lot of options, but we want to configure safe links and safe attachments so that users won't be able to receive them from outside the organization <br/>
<img src="https://i.imgur.com/GUIK91q.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>

Click on "Safe Links" and click on "Built-in protection (Microsoft)" <br/>
At the top click on "View preset security policies" <br/>
We want to turn standard protection on, so click on "Manage Protection settings" <br/>
Select "All recipients" for each section <br/>
For the Impersonation section add your employee and admin, do this by clicking on the "Add a Valid email" which will show all of your users <br/>
<img src="https://i.imgur.com/zyARYHW.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>

On the "Policy Mode" section select "Turn on policy when finished" <br/>
Click "Next" and then "Confirm" <br/>
Should see that Standard Policy Protection is now toggled on <br/>
<img src="https://i.imgur.com/ZahiUCu.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>

There should be a new Policy called "Standard Preset Security Policy" under safe links <br/>
This also applies to safe attachments, naviagte to the "safe attachments" section and verify that the "Standard Preset Security Policy" also appears there <br/>
<br/>

<h2>Anit-Phishing Policy Creation</h2>

Under the "Email and Collboration" section, click on "Policies and Rules" <br/>
Click on "Anti-Phishing" <br/>
Click on "Create" <br/>
Name it something like "Anti-phishing Policy" and click "Next" <br/>
Add your employee and Admin users then click "Next" <br/>
Check the Box for "Enable Users to protect" and click "Manage 0 Sender(s)" <br/>
Click "Add User" and add your employee and admin users <br/>
Click the "Add" button on the bottom once selected then done<br/>
<img src="https://i.imgur.com/AhMLQya.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>

The "Manage 0 Sender(s)" should then turn to show however many users you added ( Ex: Manage 2 Sender(s) ) <br/>
Check the Box for "Enable domains to protect" then check the box for "Include domains I own" <br/>
Click "Next" <br/>
<img src="https://i.imgur.com/kP9F97J.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>

Under "Message Actions" section, for "if a messagee is detected as User Impersonation" and "If as message is dected as domain impersonation" set both options as "Quarantine the message" <br/>
Set both of the "Apply Quarantine Policy" as "AdminOnlyAccessPolicy" so that only admins may view this in Defender Quarantine <br/>
Under "Safety tips and Indicators" check the box for "Show first contact safety tip" to show them a warning for new users and users they don't normally receive from <br/>
Click "Next" and Click "Submit" <br/>
Your Anti-phishing policy should now be created! <br/>
<img src="https://i.imgur.com/eG2meYe.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>

So you should see the 2 policies you created under each section (not counting any defaults that show) <br/>
<img src="https://i.imgur.com/XZ5okeJ.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>


<h2>Creating Mail flow rules</h2>

Let's Navigate to the Microsoft Exchange Admin Center so we can create some mail flow rules to cover additional points <br/>


