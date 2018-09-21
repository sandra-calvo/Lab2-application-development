# IBM Cloud Workshop :cloud:
### PART 2 

In this guide:
  - [Overview](#overview)
  - [Introduction](#introduction)
  - [PHASE 6](#phase-6): Create an application that uses custom ML model 
  - [PHASE 7](#phase-7): Connect Watson Assistant with your ML model 


#### Prerequisites
- IBM Cloud account
  - Create a free account www.bluemix.net

## Overview 

The purpose of this lab is to guide the user in the data science life cycle from raw data to an application with a machine learning model. All this using IBM Cloud tools. 

![](/images/Tools.png?raw=true)

**Part 1:** Data science and data analytics part using Watson Studio, Cloud Object Storage and Watson Machine Learning services. https://github.com/sandra-calvo/Lab1-data-science

**Part 2:** Application development section using Node-RED and Watson Assistant services to connect a web application with the machine learning model deployed in Part 1. https://github.com/sandra-calvo/Lab2-application-development


## Introduction 

**IBM Cloud** is a suite of cloud computing services from IBM that offers both platform as a service (PaaS) and infrastructure as a service (IaaS). 

<img src="/images/IBMCloud.png" width="90%" height="90%">

# PHASE 6 
## Create an application that uses custom ML model 

### Step 10. Create a Node-RED application

**Node-RED** is a visual tool for wiring the internet of things - connecting hardware devices, APIs and online services in a new and interesting way. Node-RED provides a browser-based flow editor that makes it easy to wire together flows using the wide range nodes in the palette. Flows can be then deployed to the runtime in a single-click.

1. In a browser navigate to https://bluemix.net
2.	Select 'LOG IN' then enter your log in information and press 'SIGN IN'.  You should see your dashboard. 
3.	Select the 'CATALOG' view.
![](/images/App1.png?raw=true)
4.	Locate the Node-RED started service and click on it. 
<img src="/images/App2.png" width="50%" height="50%">

5.	Enter a name for your application, as shown below (host will automatically be completed). The host name must be unique on IBM Cloud, so please choose a name with your company name or initials to try to make a unique name.  Press 'CREATE'. 
![](/images/App3.png?raw=true)
 
6.	Your application is now staging and will be up and running in a short while. Click 'OVERVIEW' to see information about your application. 
The application will be ready in a couple of minutes. If you want to check the progeress click on the _LOGS_ icon on the left side menu. 

<img src="/images/App3b.png" width="30%" height="30%">

*Note: If you are using Lite accounts your application will be in an awake mode. That means that if after 10 days your application has not been used IBM will stop it.*

7.	When fully staged, click on the _Visit app link_, next to the green or half green circle, this launches the Node-RED main page.

<img src="/images/App4.png" width="50%" height="50%">
  
8.	Configure your Node-RED editor. In this section, you will set up a username and password to protect your flow. 
<img src="/images/App5.png" width="50%" height="50%">

9.	Write an username and a password of your choice and click 'Next'. Remember that it does not have to be related to your IBM Cloud ID. 
<img src="/images/App6.png" width="50%" height="50%">
 
#### Your Node-RED flow is all set! Enter your credentials to access the editor.

<img src="/images/App8.png" width="70%" height="70%">
 
Now click Go to your Node-RED flow editor to open the flow editor.

10.	When using Node-RED we build our apps using this graphical editor interface to wire together the blocks we need. We can simply drag and drop the blocks from the left menu into the workspace in the center of the screen and connect them to create a new flow. 

Note: If you get an "Authorization denied" message when deploying your applications make your sure you are logged in. Click on the icon on the top right side of the Node-RED canvas and login with the credentials you created in the previous steps. 

### Step 11: Add new nodes to the Node-RED palette
We are going to add new nodes to the Node-RED palette directly from the Node-RED window. For this lab we need the following nodes:

      - node-red-dashboard

In the Node-RED window click on the three lines on the top right corner and in the menu, click on the "Manage palette". This will open the node menu where you can add new nodes to your application. 

<img src="/images/App23.png" width="30%" height="30%">

You will see the nodes that are installed by default and if you go to the 'install' tab you can search for any node package and add it directly to your app.

<img src="/images/App24.png" width="50%" height="50%">
             
Search for the dashboard nodes by writing 'dashboard'. This will return multiple node packages, you need to install the package 'node-red-dashboard'. Find it in the search results and click on install. 

<img src="/images/App25.png" width="50%" height="50%">
 
This will prompt a window to confirm the installation. Click on install and wait few minutes, the application may require a restart. Click "Done" to close the left side menu. 

<img src="/images/App26.png" width="50%" height="50%">

After few seconds you will see the new nodes in your Node-RED palette.

### Step 12: Import the Node-RED application flow
In this section we will build a simple flow to represent the user interface that will interact with our ML model created in Watson Studio. 

Copy the content of the **ApplicationFlow.json** file. 
Import the flow by simply clickcing on the 3 white lines on the top right corner of the Node-RED window.  Import - Clipboard.

<img src="/images/App27.png" width="50%" height="50%">

Paste the text you copied from the file. 

<img src="/images/App28.png" width="50%" height="50%">

The flow will create a new flow window named 'ML-UI'. This flow reads input data from the user and calls the ML model to give a prediction in the UI. 
![](/images/App29.png?raw=true)
 
You will need to do some editing on few nodes.
**EDIT ML CREDENTIALS**

It also possible to change the looks of your user interface in the dashboard tab. 

<img src="/images/App30.png" width="50%" height="50%">

Deploy your application changes from the Deploy button on the top right side of the screeen. 

### Step 13. Check your webapp UI! 
The dashboard nodes added an UI to our Node-RED application. To access the UI go to:
http://yourAppName.eu-gb.mybluemix.net/ui - UK

Remember that if you are in US, Germany Sydney the addredd will look slightly different:
http://yourAppName.mybluemix.net/ui - US South
http://yourAppName.eu-de.mybluemix.net/ui - Germany
http://yourAppName.au-syd.mybluemix.net/ui - Sydney

Awesome, you web app is ready! Now you can interact with the machine learning model you created from the webapp. :+1:

# PHASE 7
## Connect Watson Assistant with your ML model 

### Step X. Create Watson Assistant service on IBM Cloud
With IBM Watson™ Assistant service you can build a solution that understands natural-language input and uses machine learning to respond to customers in a way that simulates a conversation between humans.

Go to your IBM Cloud account and open the catalog. Look for Watson Assistant service and click on it.

<img src="/images/WA1.png" width="50%" height="50%">

Choose the region and space where you want the service to be created. Your organization will be filled by default.
You don't need to change the name if you don't want to, just click on 'Create'. 
![](/images/WA2.png?raw=true)

Once the service is created click on 'Launch tool' to access it. 
![](/images/WA3.png?raw=true)
 
Click on Log in with IBM ID and you will automatically access the service. It uses your IBM Cloud ID and password.

<img src="/images/WA4.png" width="50%" height="50%">

In the home tab you have videos and tutorials on how to get started building dialoges. Let's move to the Workspaces tab.

<img src="/images/WA5.png" width="50%" height="50%">
 
### Step X. Import a workspace
The natural-language processing happens inside a workspace, which is a container for all of the artifacts that define the conversation flow for an application.

You can create a workspace and start from scratch or import an existing conversation. 
Let's start by importing a conversation. Download the **MLConversation.json** file located in this repository. 

Click on the import icon shown in the image below. 

<img src="/images/WA6.png" width="50%" height="50%">

When you import a workspace, you can choose to import only the intents and entities, which can be useful if you want to build a new dialog using the same training data. In this case we will import everything.

<img src="/images/WA7.png" width="50%" height="50%">

### Step X. Test your dialog
As you make changes to your dialog, you can test it at any time to see how it responds to input.
1.	From the Dialog tab, click the conversation buble icon.
2.	In the chat panel, type some text and then press Enter.
3.	Check the response to see if the dialog correctly interpreted your input and chose the right response. 

The chat window indicates what intents and entities were recognized in the input. In the dialog editor pane, the currently active node is highlighted
Feel free to create new intents for your bot.
![](/images/WA8.png?raw=true)


### Step X. Get your credentials 
In this example, we will need your Watson Assistant credentials and your workspace ID.
Go to the deploy tab in the Assistant window. There you will find your workspace ID, username and password. Copy the credentials and save them for later.
![](/images/WA9.png?raw=true)


### Step X. Build a Node-RED flow to connect with Watson Assistant
**Back to Node-RED window**

Copy the content of **bot-ui-flow.json** and import the flow to Node-RED, same way you did in Step X.
Once you do this your flow should look like this:
![](/images/WA10.png?raw=true)

Edit the conversation node with your own credentials saved in the previous step. 

### Step X. Check the final result! 
Go back to the UI and talk with your bot! 
You can ask for sensor information and it will show in the gauge the last measurement. 
![](/screenshots/WA11.png?raw=true)
