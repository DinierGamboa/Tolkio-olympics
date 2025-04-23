# Tolkio-olympics

Olympic Data Anaytics

1. Create Storage Account in the resource group 
	- create a container and two folders: raw-data and transformed-data

2. Create Azure Data Factory
	-Create Copy Data activity
	-In the Source tab add a new source data set, in this case it's
	 a HTTP reference with DelimitedTex format. Add a new link service and Add the URL from your raw dataset on Github .
	-In the Sink tab add a new sink data set, in this case it's 
	 a Azure DataLake Storage Gen2 reference with DelimitedTex format. Add a new linked service and choose your storage account
	-Add the path and name of the file in the Storage Account
	-Validate and Debug
	-Do the same with all the datasets from your repository, and connect all your Copy Data activities, 
	 debug once all are connected to see the load in your storage account
	
	
3. Create Azure Databricks
	-create a compute
	-In azure look for app registration and create one, and copy the client ID and tenant ID
			
					Application (client) ID: d983b070-9e1a-42a7-95f3-c7f83e82d213  
					Directory (tenant) ID: 5df7bfe8-c66e-4465-9a6b-7636fd5c6dd8

	-go to Certificates and Secrets and add a client secret
					secretkey: WJm8Q~BKzIikvKqn5gfew0Xhcqm7VSpDiDe3cduW
	
	-Use these keys in the code in databricks (The vest practice is to use Key Vault)
	-We need to give permission to app registration to access the Data Lake storage account, 
	 this can be done in the folder withing the container and access control (to app01-dg in the example)
	-Usually you need to create the spark session but in databricks it's already created
	-Transform the datasets and load them in the transformed-data folder

4. Create Synapse Analytics 
	-from data create Lake Dataset and create tables with pulling the cvs files from datalake
