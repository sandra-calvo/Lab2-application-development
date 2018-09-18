# IBM Cloud Workshop :cloud:

## Introduction 
In this guide, you will:
  - [Introduction](#introduction)
  - [PHASE 1](#phase-1): Data Preparation using Data Refinery
  - [PHASE 2](#phase-2): Data analysis using Modeler
  - [PHASE 3](#phase-3): Create your custom machine learning model 
  - [PHASE 4](#phase-4): Deploy ML model 
  - [PHASE 5](#phase-5): Create an application that uses custom ML model 
  - [PHASE 6](#phase-6): Connect Watson Assistant with your ML model 
  - [PHASE 7](#phase-7): Data science with Jupyter Notebooks in Python, R or Scala


#### Prerequisites
- IBM Cloud account
  - Create a free account www.bluemix.net

# Introduction 
The purpose of this lab is to guide the user in the data science life cycle from raw data to an application with a machine learning model. All this using IBM Cloud tools. 

**IBM Cloud** is a suite of cloud computing services from IBM that offers both platform as a service (PaaS) and infrastructure as a service (IaaS). 

<img src="/images/IBMCloud.png" width="90%" height="90%">

**Watson Studio** is an integrated environment designed to make it easy to develop, train, manage models and deploy AI-powered applications. It is a solution delivered on the IBM Cloud. Watson Studio provides a suite of tools for data scientists, application developers and subject matter experts to collaboratively and easily work with data.

![](/images/Tools.png?raw=true)

In the picture above you can see the collection of IBM Cloud tools we are going to use in this workshop:

      - Watson Studio  - Data science, ML
      - Cloud Object Storage -  Storage
      - Watson Machine Learning - ML Model deployment
      - Node-RED - Application logic
      - Watson Assistant - Bot service integration 


# PHASE 1
## Data Preparation using Data Refinery

**Data Refinery** it’s a self-service data preparation client for data scientists, data engineers, and business analysts. With it, you can quickly transform large amounts of raw data into consumable, quality information that’s ready for analytics. Data Refinery makes it easy to explore, prepare, and deliver data that people across your organization can trust.

## Step 1: Create a Watson Studio Project
Before we start with the data preparation we need to create a project in Watson Studio. In order to create a project login to Watson Studio: https://eu-gb.dataplatform.ibm.com/ 

To create a project with all tools click on the _New Project_ icon in the dashboard. 
![](/images/Picture1.png?raw=true)

Next you will see the different types of projects available in Watson Studio. For this lab we will use the _Complete_ project. Select that and click on _OK_.

<img src="/images/Picture2.png" width="60%" height="60%">

On the New project screen, add a name and optional description for the project.
You could restric who can be a collaborator. For example, if you want to restrict the project to internal users for security reasons. In this case we don't need to apply any restrictions. 
Choose whether to restrict who you can add as a collaborators. You can't change this setting after you create the project.

<img src="/images/Picture3.png" width="80%" height="80%">

Every project needs a Cloud Object Storage service associated. **Cloud Object Storage** is storage for the cloud. Essentially a key-value store, files (or any binary data) are given an identifying key (or name) and stored as an 'object' in a uniquely named 'bucket' or 'container'. 

Click _Add_ to connect with your existing instance or to create a new one. If you have an existing Object Storage instance select the "Existing" tab and connect with your instance. If you need to create a new Object Storage select the pricing plan, in this case Lite, the free plan, is enough. Then click on _Create_.

<img src="/images/Picture4.png" width="80%" height="80%">

A new window will be prompted to confirm the creating of the service. Confirm the plan is Lite, resource group is default and you can edit the name of the service if you want. When you are ready click on _Confirm_.

<img src="/images/Picture5.png" width="50%" height="50%">

Click on _Refresh_ and you will see the Cloud Object Storage service associated with the project. Click on _Create_.
![](/images/Picture6.png?raw=true)

Your project is ready! 👍

## Step 2: Add data to your project

After you create a project, you add data assets to it so that you can work with data. All the collaborators in the project are automatically authorized to access the data in the project. 
You can add data assets from these sources to legacy projects:

    Local files
    Community
    Database connections
    
In this lab we will add a simple .csv file from our local collection. Download the file from this link: **BOX LINK WITH THE DATA SET** Password will be delivered during the workshop. 

From your project's _Assets_ page, click the Find and add data icon (<img src="/images/Icon1.png" width="3%" height="3%">).

Browse the file or drag them onto the Load pane.
![](/images/Picture7.png?raw=true)

The files are saved in the object storage that is associated with your project and are listed as data assets on the Assets page of your project.

## Step 3: Data refinery

Refining data consists of cleansing and shaping it. When you cleanse data, you fix or remove data that is incorrect, incomplete, improperly formatted, or duplicated. And when you shape data, you customize it by filtering, sorting, combining or removing columns, and performing operations.

As you manipulate your data, you build a customized data flow that you can modify in real time and save for future re-use. When you save the refined data set, you typically load it to a different location than where you read it from. In this way, your source data can remain untouched by the refinement process.

If you want to be able to save refined data to cloud or on-premises data sources, create connections for this purpose. Source connections can only be used to read data; target connections can only be used to load (save) data. 

In this lab we will create a new .csv file with our refined data set. 

Open Data Refinery by clicking Tools > Data Refinery.

<img src="/images/DR1.png" width="30%" height="30%">

Select the project you want to work in and then click _Select Data_ to select the data you want to work with.

<img src="/images/DR2.png" width="100%" height="100%">

On the Data tab, apply operations to cleanse, shape, and enrich your data. You can enter R code in the command line and let autocomplete assist you in getting the syntax right. Or you can use the Operations menu to browse operation categories or search for a specific operation, then let the UI guide you.

<img src="/images/DR3.png" width="30%" height="30%">

**--> OPERATIONS TO THE SAMPLE DATA DESCRIBED**

Validate your data throughout the data refinement process.
Use visualizations to gain insights into your data and to uncover patterns, trends, and correlations within your data.

When you've refined the sample data set to suit your needs, click the _Run data flow_ icon in the toolbar to run the data flow on the entire data set.

By default, Data Refinery uses the name of the data source to name the data flow and the target data set. You can change these names, but you can't change the project that these data assets belong to.

a. In the Data flow details pane, optionally edit the name of the data flow and enter a description for it. You can also add a one-time or repeating schedule for the data flow.

b. In the Data flow output pane, optionally edit the name of the target data set and enter a description for it. You can save the target data set to the project, to a connection, or to a connected data asset . If you save it to the project, you can save it as a new data asset (by default) or you can replace an existing data asset. To save the target data set to a connection or as a connected data asset or to replace an existing data asset, use Change Location.

Click _Save and Run_.

**SANDRA** https://dataplatform.cloud.ibm.com/docs/content/refinery/refining_data.html?context=analytics&linkInPage=true

# PHASE 2
## Data analysis using Modeler
**Modele: Flow editor** You can create a machine learning flow, which is a graphical representation of a data model, or a deep learning flow, which is a graphical representation of a neural network design, by using the Flow Editor. Use it to prepare or shape data, train or deploy a model, or transform data and export it back to a database table or file.

## Step 4: 

## Step 5:

# PHASE 3
## Create your custom machine learning model

## Step 6:

# PHASE 4
## Deploy ML model
**IBM Watson Machine Learning** is a full-service IBM Cloud offering that makes it easy for developers and data scientists to work together to integrate predictive capabilities with their applications. The Machine Learning service is a set of REST APIs that you can call from any programming language to develop applications that make smarter decisions, solve tough problems, and improve user outcomes.

## Step 7: Create a Watson machine learing service

To design, train, and deploy machine learning models in IBM Watson Studio, you need to associate an IBM Watson Machine Learning service instance, as well as some supporting services (such as IBM Cloud Object Storage), with a project.

Services are added in the _Settings_ page of your project in Watson Studio.

<img src="/images/Model1.png" width="70%" height="70%">

Click _Add service_ under Associated Services and choose Watson.

<img src="/images/Model2.png" width="100%" height="100%">

Select Watson Machine Learning from the Catalog and click _Add_.

<img src="/images/Model3.png" width="100%" height="100%">

If you already have a service created in IBM Cloud you can connect that to your project in the _Existing_ tab. In this case we are going to create a new machine learning instance. 
Select the Lite plan, for this workshop the free plan will be enough. Then click on _Create_.

<img src="/images/Model4.png" width="100%" height="100%">

You will need to confirm the creation of the service. In this step it is possible to change the name of the service. Feel free to edit the name and then click on _Confirm_.

<img src="/images/Model5.png" width="50%" height="50%">

Great! You created a Watson Machine Learning service and associated it with your Watson Studio project. In the list of services connected to the project you should see now Watson machine learning. 

<img src="/images/Model6.png" width="70%" height="70%">

## Step 8: Deploy the ML model

## Step 9: Test the ML model


# PHASE 5
## Create an application that uses custom ML model 

## Step 10. Create a Node-RED application

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
*Note: If you are using Lite accounts your application will be in an awake mode. That means that if after 10 days your application has not been used IBM will stop it.*
![](/images/PictureX.png?raw=true)

7.	When fully staged, click on the View app link, next to the green or half green circle, this launches the Node-RED main page. 
![](/images/App3b.png?raw=true)

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

## Step 11: Add new nodes to the Node-RED palette
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

## Step 12: Import the Node-RED application flow
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

## Step 13. Check your webapp UI! 
The dashboard nodes added an UI to our Node-RED application. To access the UI go to:
http://yourAppName.eu-gb.mybluemix.net/ui - UK

Remember that if you are in US, Germany Sydney the addredd will look slightly different:
http://yourAppName.mybluemix.net/ui - US South
http://yourAppName.eu-de.mybluemix.net/ui - Germany
http://yourAppName.au-syd.mybluemix.net/ui - Sydney

Awesome, you web app is ready! Now you can interact with the machine learning model you created from the webapp. :+1:

# PHASE 6
## Connect Watson Assistant with your ML model 

## Step X. Create Watson Assistant service on IBM Cloud
With IBM Watson™ Assistant service you can build a solution that understands natural-language input and uses machine learning to respond to customers in a way that simulates a conversation between humans.

Go to your IBM Cloud account and open the catalog. Look for Watson Assistant service and click on it.

<img src="/images/Picture31.png" width="50%" height="50%">

Choose the region and space where you want the service to be created. Your organization will be filled by default.
You don't need to change the name if you don't want to, just click on 'Create'. 
![](/images/Picture32.png?raw=true)

Once the service is created click on 'Launch tool' to access it. 
![](/images/Picture33.png?raw=true)
 
Click on Log in with IBM ID and you will automatically access the service. It uses your IBM Cloud ID and password.

<img src="/images/Picture34.png" width="50%" height="50%">

In the home tab you have videos and tutorials on how to get started building dialoges. Let's move to the Workspaces tab.

<img src="/images/Picture35.png" width="50%" height="50%">
 
## Step X. Import a workspace
The natural-language processing happens inside a workspace, which is a container for all of the artifacts that define the conversation flow for an application.

You can create a workspace and start from scratch or import an existing conversation. 
Let's start by importing a conversation. Download the **MLConversation.json** file located in this repository. 

Click on the import icon shown in the image below. 

<img src="/images/Picture36.png" width="50%" height="50%">

When you import a workspace, you can choose to import only the intents and entities, which can be useful if you want to build a new dialog using the same training data. In this case we will import everything.

<img src="/images/Picture37.png" width="50%" height="50%">

# Step X. Test your dialog
As you make changes to your dialog, you can test it at any time to see how it responds to input.
1.	From the Dialog tab, click the conversation buble icon.
2.	In the chat panel, type some text and then press Enter.
3.	Check the response to see if the dialog correctly interpreted your input and chose the right response. 

The chat window indicates what intents and entities were recognized in the input. In the dialog editor pane, the currently active node is highlighted
Feel free to create new intents for your bot.
![](/images/Picture38.png?raw=true)


# Step X. Get your credentials 
In this example, we will need your Watson Assistant credentials and your workspace ID.
Go to the deploy tab in the Assistant window. There you will find your workspace ID, username and password. Copy the credentials and save them for later.
![](/images/Picture39.png?raw=true)


## Step X. Build a Node-RED flow to connect with Watson Assistant
**Back to Node-RED window**

Copy the content of **bot-ui-flow.json** and import the flow to Node-RED, same way you did in Step X.
Once you do this your flow should look like this:
![](/images/Picture41.png?raw=true)

Edit the conversation node with your own credentials saved in the previous step. 



## Step X. Check the final result! 
Go back to the UI and talk with your bot! 
You can ask for sensor information and it will show in the gauge the last measurement. 
![](/screenshots/Picture42.png?raw=true)


# PHASE 7
## Data science with Jupyter Notebooks in Python, R or Scala
A Jupyter notebook is a web-based environment for interactive computing. You can run small pieces of code that process your data, and you can immediately view the results of your computation. Notebooks include all of the building blocks you need to work with data:

    The data
    The code computations that process the data
    Visualizations of the results
    Text and rich media to enhance understanding
