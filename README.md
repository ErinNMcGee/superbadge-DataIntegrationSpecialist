# superbadge-DataIntegrationSpecialist



-Chalange 1

Step 1 : Install the pkg ==> https://login.salesforce.com/packaging/installPackage.apexp?p0=04t41000001T3kx

Step 2 : Create Remote site
Remote site name:-	BillingService
Remote site URL:-	http://sb-integration-bs.herokuapp.com
Active :- 	Checked

Step 3 : Add vales in ServiceCredentials customsetting    
Go to Setup => develop => customsetting => click "ServiceCredentials " => click manage and Enter Below data
name:-  BillingServiceCredential
Username:-	bsUser1
Password	:- bsPass1

Step 4: Create Named Credential 
Label:	ProjectService
Name:	ProjectService
URL:	https://sb-integration-pms.herokuapp.com/projects
Identity Type:	Named Principal
Authentication Protocol:	Password Authentication
Username:	pmsUser1
Password:	pmsPass1
Generate Authorization Header:	Checked

-Chalange 2

Step 1: Create Connected App
Connected App Name:	ProjectService
API Name:	ProjectService
Contact email:	Your email
Enable OAuth Settings:	Checked
Callback URL:	https://sb-integration-pms.herokuapp.com/oauth/_callback
Selected OAuth Scopes:	Full access & Perform requests on your behalf at any time (refresh_token, offline_access)

Step 2: get the security token by register ur org on heroku app @  https://sb-integration-pms.herokuapp.com
  a)go to like -  https://sb-integration-pms.herokuapp.com
  b)validate ur identity by login into sf org
  c)enter consumer key and consumer secret genrate from connected app in above step
  d)click test connected app
  e)copy token -> go to custom setting -> open serviceTokens -> click manage -> new ->
  f)name = ProjectServiceToken
  g)token = ur copied toke value

-Chalange 3 & 4

Step1 : copy the code of below mention classes in respective files.
a)ProjectCalloutService
b)ProjectCalloutServiceMock
c)ProjectCalloutServiceMockFailure
d)ProjectCalloutServiceTest 

git link of code - https://github.com/amitjpr/superbadge-DataIntegrationSpecialist

Step 2 : run the test class

Step 3,4,5 is not required for challenge 

Step 3 : add "New Project" as a value in type field of opportunity

step 4 : Add the following values to opportunity Stage.

Stage Name	        Probability 	Type
Submitted Project 	100	          Closed/Won
Resubmit Project  	100	          Closed/Won


Step 5  :  Create process builder on opportunity Object
setup-> process builder-> new
Process name = Update Opportunity

select object = opportunity 
start the process when a record is created or edited
folow the instruction on requirement in superbadge page to create process builder


-Chalange 5 & 6

Step1 : copy the code of below mention classes in respective files.
a)ProjectRESTService 
b)ProjectRESTServiceTest 

git link of code - https://github.com/amitjpr/superbadge-DataIntegrationSpecialist

Step 2 : run the test class

-Chalange 7
Step 1 : get the wsdl from http://sb-integration-bs.herokuapp.com/ws/invoices.wsdl
and genrate classes from this wsdl and name the class "BillingServiceProxy"

Step2 : copy the code of below mention classes/trigger in respective files.
a)ProjectTrigger 
b)BillingCalloutService

git link of code - https://github.com/amitjpr/superbadge-DataIntegrationSpecialist


-Chalange 8

Step1 : copy the code of below mention classes in respective files.
a)BillingCalloutServiceMock 
b)BillingCalloutServiceMockFailure
c)BillingCalloutServiceTest

git link of code - https://github.com/amitjpr/superbadge-DataIntegrationSpecialist
Step 2 : run the test class

-Chalange 9 
Step 1 : create external data source
setup-> develop - > external data source -> new external data source

External Data Source	BillingService
Name	BillingService
Type	Salesforce Connect OData 2.0
URL	https://sb-integration-is.herokuapp.com/odata
Identity Type	Anonymous
Authentication Protocol	No Authentication

Step 2: after creating click on "validate and sync" -> select invoice -> click "sync"

step 3 : change the field type to "Indirect Lookup field" of "projectref__c" field of invoice object
steup-> develop->external object - > invoice -> projectref__C -> edit -> change field type -> select indirect lookup -> related to "project" -> target "projectref__c" ->save

step 4: update project object layout
open project object def -> open layout in edit mode -> add invoice related list

step 5: update invoice related list
The related list should only display: External ID, Bill Amount, and Bill Date.







