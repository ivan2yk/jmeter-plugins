# Configurations

- **[Azure AD Credential](#azure-ad-credential)**  
    Configuration for authentication and authorization by Azure AD.
- **[Azure Service Bus Connection](#azure-servicebus-connection)**
    Create a connection to the Azure Service Bus.

## Azure AD Credential

This is the configuration for authentication and authorization by Azure AD.

### How to install

Download jmeter-plugins-azure-ad.?.?.?.jar file from [latest release](https://github.com/pnopjp/jmeter-plugins/releases/latest) and put it into lib/ext directory of JMeter \(e.g. /usr/local/jmeter/lib/ext\), then restart JMeter.
> Some plugins include the classes contained in this jar file.

### Common parameters

|Attribute|Description|Required|
|-----|-----|-----|
|Name|Descriptive name for this sampler that is shown in the tree|No|
|Variable Name for created credential|Variable name bound to credential. This needs to uniquely identify the configuration. It is used by the Samplers to identify the configuration to be used.|Yes|
|Credential type|Types of credentail.|Yes|
|Authority host|Specifies the Azure Active Directory endpoint to acquire tokens.<br />For general Microsoft Azure, select "login<span></span>.microsoft.online.com". For the Azure Government or Azure China 21Vianet, etc., select the appropriate endpoint.|Yes|

### Parameters for each credential type

The parameters to be set for each credential type are different.

#### Client certificate

|Attribute|Description|Required|
|-----|-----|-----|
|Tenant Id|Azure AD tenant Id.|Yes|
|Client Id|Client \(Application\) Id of Azure AD application.|Yes|
|File type|Certification file type. \(PEM or PFX\)|Yes|
|Filename|Certification file name.|Yes|
|Password|Password for certification file.|No|

#### Client secret

|Attribute|Description|Required|
|-----|-----|-----|
|Tenant Id|Azure AD tenant Id.|Yes|
|Client Id|Client \(Application\) Id of Azure AD application.|Yes|
|Client Secret|Client secret for Azure AD application.|Yes|

#### Managed identity

|Attribute|Description|Required|
|-----|-----|-----|
|Client Id|Client \(Application\) Id of Azure AD application.|No|

### Sample files

- [AzEventHubsSampler.jmx](../samples/AzEventHubsSampler.jmx)  
    Use in testing to Azure Event Hubs

## Azure Service Bus Connection

Create a connection to the Azure Service Bus with the settings specified in this.  
The connection created by this configuration will be used by the "Azure Service Bus Sampler".  

Works with Apache JMeter™ v5.4.1 or later.

### How to install

Download jmeter-plugins-azure-servicebus.?.?.?.jar file from [latest release](https://github.com/pnopjp/jmeter-plugins/releases/latest) and put it into lib/ext directory of JMeter \(e.g. /usr/local/jmeter/lib/ext\), then restart JMeter.
> Some plugins include the classes contained in this jar file.

### Parameters

|Attribute|Description|Required|
|-----|-----|-----|
|Name|Descriptive name for this sampler that is shown in the tree|No|
|Service Bus Namespace|Azure Service Bus namespace name to send messages to.<br />(e.g. YOURSERVICEBUS<span></span>.servicebus.windows.net\)|Yes|
|Send messages to|Choose whether to send the messages to the "Queue" or to the "Topic".|Yes|
|Queue name / Topic name|Queue/Topic name to send messages to.|Yes|
|Protocol|Protocol for sending messages|Yes|
|Auth Type|Authorization type to use when sending messages to Azure Event Hubs.<br />If you select "Azure AD credential", also define the Azure AD Credential Config Element.|Yes|
|Shared Access Policy [\*1](#1-servicebus)|Shared access policy name of the Event Hubs namespace or Event Hub.|Yes|
|Shared Access Key [\*1](#1-servicebus)|Shared access keys for the shared access policy|Yes|
|Variable Name of credential declared in Azure AD Crednetial|The variable name of the credential declared in Azure AD Credential, specified, if "Azure AD credential" is selected for "Auth Type".|Yes|
|Variable name for created connection|The name of the connection to create.|No|

<span id="1-servicebus">\*1</span>: If "Shared access signature" is selected for Auth type, set these parameters.

### Sample files

- [AzServiceBusSampler.jmx](../samples/AzServiceBusSampler.jmx)

### Tutorial

- [How to request to Azure Service Bus by Apache JMeter™](https://blog.pnop.co.jp/jmeter-azure-service-bus_en/)
