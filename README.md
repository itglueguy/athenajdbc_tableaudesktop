## Requirements for athena.properties files implementation for Tableau Desktop
- The format is one key value pair per a line with no delimiters
- Paths with "\" in the line can be escaped with "\\" for windows based paths
- It can be inferred from the Athena Simbda JDBC Documentation is that if you simply make sure all keypairs have their own lines and no delimiters (";") you can reasonable convert the files accordingly

## FAQ
### Where are athena.properties files normally located?
- Windows - Under the My Tableau Repository/Datasourcfes

### What Should be included in order to use Environmental Variables in the athena.properties File?
- It will allow you to use the Key, Secret Key, and Token
- The file contents is simply: AwsCredentialsProviderClass=com.simba.athena.amazonaws.auth.DefaultAWSCredentialsProviderChain

### What is Example of the Azure AD Provider?

It shows up this way int he AWS Simba JDBC Athena Documentation for connection to SQL Workbench:

jdbc:awsathena://AwsRegion=us-east1;S3OutputLocation=
s3://test;AwsCredentialsProviderClass=com.
simba.athena.
iamsupport.plugin.AzureCredentialsProvider;UID=jsmi
th@
acme.com;PWD=simba12345;tenant_id=xyz;client_
id=xyz;
client_secret=xyz

It can than be converted to in Tableau:

AwsRegion=us-east1
S3OutputLocation=s3://test;AwsCredentialsProviderClass=com.simba.athena.iamsupport.plugin.AzureCredentialsProvider
UID=jsmith@acme.com
PWD=simba12345
tenant_id=xyz
client_id=xyz
client_secret=xyz




### What is an Example of the Browser Azure AD Provider?

It show up this way in the AWS Simba JDBC Athena Documentation for connection to SQL Workbench:

jdbc:awsathena://AwsRegion=us-east1;S3OutputLocation=
s3://test;AwsCredentialsProviderClass=com.
simba.athena.
iamsupport.plugin.BrowserAzureCredentialsProvider;U
ID=
jsmith@acme.com;PWD=simba12345;tenant_id=xyz;
client_id=xyz;client_secret=xyz

It can than be converted to in Tableau:

AwsRegion=us-east1
S3OutputLocation=s3://test
AwsCredentialsProviderClass=com.simba.athena.iamsupport.plugin.BrowserAzureCredentialsProvider
UID=jsmith@acme.com
PWD=simba12345;tenant_id=xyz
client_id=xyz
client_secret=xyz


## Reference

- https://github.com/geordielad/tableau-athena-credential-provider-examples
