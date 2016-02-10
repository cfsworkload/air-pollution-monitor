# Air Pollution Monitor

## Leverage FIWARE IoT sensor data to monitor air pollution in Santander

The Air Pollution Monitor app demonstrates how air pollution sensor data can be ingested into Bluemix using FIWARE IoT APIs, and then processed, stored and visualized using **Node-RED**, **Cloudant**, **dashDB** and **Embeddable Reporting** services.

## Introduction
The Air Pollution Monitor sample app has been created so you can deploy it into your personal DevOps space after signing up for Bluemix and DevOps Services. When you deploy the pipeline to Bluemix, an instance of **Cloudant NoSQL Database"**, **DashDB**, and **Embeddable Reporting** services will be automatically provisioned, configured and bound to your app. When the app is launched, you will provide your FIWARE Lab credentials, which will be used to start retrieving live sensor data from the Lab, process it, store, and visualize. The results are displayed in an augmented map or bar chart in the web app.

## Create accounts and log in

- Sign up for Bluemix at https://console.ng.bluemix.net and DevOps Services at https://hub.jazz.net.
When you sign up, you'll create an IBM ID, create an alias, and register with Bluemix.
- Sign up for a FIWARE Lab account at https://account.lab.fiware.org/.

## Deploy to Bluemix

Select the **Deploy to Bluemix** button below to fork a copy of the project code and create the services.

  [![Deploy to Bluemix](https://bluemix.net/deploy/button.png)](https://bluemix.net/deploy?repository=https://hub.jazz.net/git/cfsworkload/fiware-app-build)

## Monitor deployment

After the pipeline has been configured, you can monitor the deployment in DevOps Services.

1. In DevOps Services, click **MY PROJECTS** and select your newly created project.
2. Click **BUILD & DEPLOY**.
3. Select **View logs and history** to monitor the deployment stages.

Once the deployment finishes, you will have an instance of the app in your Bluemix Dashboard.

## How the app works

1. Go to the web interface of the app by clicking the **Open the Deployed App** button in DevOps Services or the **Open URL** button in your Bluemix Dashboard.
2. Enter your FIWARE Lab credentials.
3. The live pollution levels in Santander can be viewed in several different ways. You can also see a history of the air pollution data aggregated since your app started running. View the data:
  - On your augmented map.
  - By going to the Node-RED flow editor, linked at the bottom of the app landing page. From here you can learn about the app implementation details and experiment with the app components and services. Some potential customization points include:
    - The query used to retrieve data in the function node.
    - The interval at which data is retrieved in the inject node. The default is 10 minutes.
    - The template node that creates the visualization.
4. Optional: From the Bluemix Dashboard, go to the UI of the Embeddable Reporting service instance associated with your app to change the report definitions. The defaults are stored in `fidef_spec.xml`.


## About the services

#### Quickly and intuitively program the app data intake and processing using Node-RED flows
Node-RED is a Node.js based application platform providing a visual flow editor, as well as a library of pre-canned 'nodes' that can be used to program data ingestion and processing flows very quickly. In the app, Node-RED is used for several purposes, including:
- Data ingestion from FIWARE Lab using NGSI-based queries.
- Pre-processing of data, programmed in javascript, including the extraction of relevant fields, validation of received values, format transformation, etc.
- Web serving, including the landing pages, as well as the rendering of an augmented map and a historical report produced by the app.
- Routing of data between intake, processing, storage and visualization.

For more information about Node-RED, go to the [Bluemix documentation](https://www.ng.bluemix.net/docs/starters/Node-RED/nodered.html).

#### Easily store and access semi-structured data using Cloudant NoSQL Database
The Cloudant NoSQL Database service provides a convenient, feature-rich NoSQL database. In the app, Cloudant is used as a short-term storage of sensor data, used for map-based visualization of live air pollution metrics.

For more information about Cloudant, go to the [Bluemix documentation](https://www.ng.bluemix.net/docs/services/Cloudant/index.html).

#### Create a data warehouse with the dashDB service

The dashDB service provides a powerful relational database with a variety of enterprise-grade features and capabilities. The app uses dashDB for long-term warehousing of sensor data, enabling sophisticated queries used to generate historical reports.

For more information about dashDB, go to the [Bluemix documentation](https://www.ng.bluemix.net/docs/services/dashDB/index.html).

#### Generate sophisticated reports with Embeddable Reporting service
The Embeddable Reporting service delivers the power of Cognos reports to Bluemix apps. The app uses the Embeddable Reporting service to generate historical reports of air pollution in Santander, leveraging the data stored in dashDB.

For more information about Embeddable Reporting, go to the [Bluemix documentation](https://www.ng.bluemix.net/docs/services/EmbeddableReporting/index.html).