# Office 365 Service Flow Connector
A Microsoft Flow connector to connect to the Office 365 Service Communications API

This Flow custom connector allows you to connect to the Office 365 Service Communications API and query the following from the API:

* Get Services: Get the list of subscribed services
* Get Current Status: Get current service status including any incidents
* Get Historical Status: Get historic service status including any incidents
* Get Messages: Get Incidents, Planned Maintenance, and Message Centre communications.

As it's a connector for Flow you only need to configure authentication in a single place and actions can be reused multiple times across Flows.

## Set Up

Before you can use the connector, you will need to create an Azure AD application and assign permissions to be able to read the Office 365 service.

### Create Azure AD application

1.	Login to Azure at https://portal.azure.com
2.	Under **Azure Active Directory**, go to **App registrations** and select **New registration**
3.	Give the application a **name** and set as **Single Tenant** and select **Register**
![](https://www.lee-ford.co.uk/images/office-365-service-flow-connector/RegisterApplication1.png)
4.	Make a note of the **Application (Client) ID** for the Flow connector
![](https://www.lee-ford.co.uk/images/office-365-service-flow-connector/RegisterApplication2.png)
5.	Under **API Permissions**, assign the **ServiceHealth.Read Application permission** under **Office 365 Management APIs**
![](https://www.lee-ford.co.uk/images/office-365-service-flow-connector/RegisterApplication3.png)
![](https://www.lee-ford.co.uk/images/office-365-service-flow-connector/RegisterApplication4.png)
6.	Under **Certificates and secrets**, create a **New client secret**. Once created make a note of the **Client secret** for the Flow connector
![](https://www.lee-ford.co.uk/images/office-365-service-flow-connector/RegisterApplication5.png)
![](https://www.lee-ford.co.uk/images/office-365-service-flow-connector/RegisterApplication6.png)
7.	Leave the page open as you will need one further change after importing the connector

### Importing Flow Connector

1.	Either clone download the connector .json file
2.	Login to https://flow.microsoft.com
3.	Under **Data**, select **Custom connector**
4.	Select **New custom connector** and **Import an OpenAPI file**
![](https://www.lee-ford.co.uk/images/office-365-service-flow-connector/CustomConnector1.png)
5.	Give the connector a **name** e.g. Office 365 Service and select the .json file
![](https://www.lee-ford.co.uk/images/office-365-service-flow-connector/CustomConnector2.png)
6.	Under **Security**, enter the **Application (Client) ID** and **Client secret** you took note of earlier. Set the **Resource URL** to https://manage.office.com and select **Create connector**
![](https://www.lee-ford.co.uk/images/office-365-service-flow-connector/CustomConnector3.png)
7.	The **Redirect URL** should now be populated in the **Security** section. Copy this
![](https://www.lee-ford.co.uk/images/office-365-service-flow-connector/CustomConnector4.png)
8.	Go back the **Azure AD application** and select **Redirect URI**. Add the copied URL and put this as a **Web URI**
![](https://www.lee-ford.co.uk/images/office-365-service-flow-connector/RegisterApplication7.png)
![](https://www.lee-ford.co.uk/images/office-365-service-flow-connector/RegisterApplication8.png)

### Using the Flow Connector

1.	Create a Flow and actions should be found under the **Custom** connector type
![](https://www.lee-ford.co.uk/images/office-365-service-flow-connector/SampleFlow1.png)
2.	When you select an action for the first time, you will be prompted to sign in with as a user to authenticate against the Azure AD application
![](https://www.lee-ford.co.uk/images/office-365-service-flow-connector/SampleFlow2.png)
![](https://www.lee-ford.co.uk/images/office-365-service-flow-connector/SampleFlow3.png)
3.	The connector should now work as intended
![](https://www.lee-ford.co.uk/images/office-365-service-flow-connector/SampleFlow4.png)