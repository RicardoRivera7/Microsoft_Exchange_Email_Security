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
On the left Under "Mail Flow" click on "Rules" <br/>
We're gonna add 2 rules, first we're gonna make a rule to flag external emails <br/>
<br/>
<br/>

At the top click "Add rule" then "Create new rule" <br/>
Name it "Flag External Emails" <br/>
Under "Apply this rule if" on the left side select "The sender" and on the right select "is External/Internal" <br/>
This will create a new section called "Select sender location", pick "Outside the organization for this" <br/>
Under the "Do the following" on the left side select "Apply a disclaimer to the message" and on the right select "prepend a disclaimer" <br/>
There should now be blue text that says "Enter Text", click on it <br/>
Add this text "Warning: This email has originated from outside the organization! Please verify the sender before clicking links or attachments" and click "Save" <br/>
There should be blue text that also says "Select One", Click on it and choose "Wrap" <br/>
<img src="https://i.imgur.com/CS6GcNt.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>

Click "Next" <br/>
Select "Severity" and choose "High" <br/>
Check the box for "Activate this rule on" <br/>
Click "Finish" <br/>
Now you have your first rule, this checks if the sender is out of the organization, if it is it sends a warning messsage to the user advising them caution <br/>
<img src="https://i.imgur.com/r6wIZVH.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>

Let's make our second rule to block executable attachments <br/>
Create a new rule <br/>
In the name field call it "Block Executable Attachments" <br/>
Under "Apply this rule if" on the left side select "Any Attachment" and on the right side select "File extension includes these words" <br/>
This will create a new section called "Specify words or phrases" where we want to block anything that can be an executable <br/>
You will have to add them indivdually, after typing one word click "Add" then repeat the process <br/>
Add these words: exe, bat, js, zip <br/>
Click "Save" <br/>
<img src="https://i.imgur.com/FJ69GpS.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>

Under "Do the following" on the left side select "Redirect the message to" and on the right side select "hosted quarantine" <br/>
This will send any message it detects with exe, js, or bat extension to the Defender Quarantine Mailbox <br/>
Click "Next" <br/>
Under "Severity" select "High" <br/>
Check the box for "Activate this rule on" <br/>
Click "Finish" <br/>
You should now see the two mail flow rules you created! <br/>
<img src="https://i.imgur.com/ApUqIKs.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>

<h2>Testing and Validating Rules</h2>

Go to Microsoft outlook and login to either your employee or admin account <br/>
If it's your first time logging in go through the first time account setup process (this is where your saved passwords will come in handy) <br/>
Once done navigate to your inbox <br/>
Go to your Microsoft 365 admin center, find the usser you want to send mail to and copy their associated username under the "Username" section <br/>
Use a seperate email account that is not part of any of your users or organization, for example I made a new gmail account so that I could send mail to my employee user (for now I'll refer to this as the gmail user) <br/>
On the seperate gmail compose a new email, we'll need to test different scenarioes, so just pure text for this first one <br/>
In the subject type something like "testing" and in the body put something similar <br/>
Send it <br/>
<img src="https://i.imgur.com/M0Gs6Gb.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>

Go back to your admin/employee outlook and check to see the email you just got <br/>
You should see the warning message and below that you should see the body text that was sent by the gmail user <br/>
That meaans our "Flag External Email" rule was successful! <br/>
<img src="https://i.imgur.com/GWNJ2Ac.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>

Now we need to test our second secnario, sending a suspicious link in the body of the email <br/>
First name the subject something like "TestLink" <br/>
Now get any link that you know is safe, I did https://www.youtube.com/ <br/>
Don't just paste the link, add the link as a hyperlink (Ex: in gmail click the "Insert Link" at the bottom of the email) <br/>
Send it <br/>
<img src="https://i.imgur.com/WkWTeAB.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>

Go to your outlook email, you should get the email along with the warning message and the link <br/>
Either hover over the link with your mouse or copy paste the link address (If hovering you should see the link at the bottom of your screen) <br/>
You should notice that the link was rewritten with safe links, its not just "https://www.youtube.com/" but instead "https://nam09.safelinks.protection.outlook.com/?url=https%3A%2F%2Fwww.youtube.com%" (It's longer just didn't want to take up too many lines) <br/>
This is proof safe links is working as intended and ensuring that links are secure by rewritting them! <br/>
<img src="https://i.imgur.com/voqF8So.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>

Now lets test our third scenario by adding a file like a text file <br/>
I created a notepad file called test.exe (not an actual executable) <br/>
Name your subject something like "testfile" <br/>
Attach it and send it <br/>
<img src="https://i.imgur.com/T0nfrx6.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>

Go to your outlook and next to the file you should see that there is an arrow, click on it <br/>
There should be a preview option, proof that Safe attachments is working since it gives you a safe preview mode <br/>
Safe Attachments works! <br/>
<img src="https://i.imgur.com/uKeBqwP.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>

Now lets test our final scenario by adding an executable attachment like a exe <br/>
Recall the mail flow rule we made called "Block Executable Attachments", the last scenario technically should have been blocked with this rule <br/>
We set it so that it should be quarantined, unfortunatley with our trial we can't really set up a quarantine properly so it just falls through <br/>
But with an actual environment, everything would be sent to quarantine for admins to review and safe attachment would work as a failguard in case anything slipped through <br/>
<br/>
<br/>

Let's make a slight change to our mail rule "Block Executable Attachments" in the Exchange admin <br/>
Click on the rule and at the top click "Edit rule Conditions" <br/>
Under "Do the following" on the left side select "Block the Message" and on the right side select "Reject the message and include an explanation" <br/>
A new section "Specify rejection reason" should appear, type "Flagged as being suspicious" <br/>
Click "Save" <br/>
<img src="https://i.imgur.com/R7WvTHQ.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>

This updated rule will just outright block any attachments instead of trying to send them for review and quarantine <br/>
<br/>
<br/>

Either find or make your own exe file and zip it up since gmail doesn't allow exe to be sent <br/>
Name the subject something like "TestingAttachment" <br/>
No need to put anything in the body, just attach the zip file that contains the exe <br/>
Send it <br/>
<img src="https://i.imgur.com/BPse9kn.png" height="80%" width="80%" alt="ExchangeSecurity"/>
<br/>
<br/>

Go to your outlook email, wait a bit and you should not receive any email <br/>
That means the block rule has worked <br/>
<br/>

You have successfully implemnted Microsoft Exchange Security policies and rules! <br/> 

