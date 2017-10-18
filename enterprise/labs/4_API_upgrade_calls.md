* Use the API on the command line to:
  * Report the latest available version of the API
```
curl -u dboyer-ibm:cloudera "http://ec2-52-212-24-11.eu-west-1.compute.amazonaws.com:7180/api/version"
v14
```
  * Report the CM version
```
curl -u dboyer-ibm:cloudera "http://ec2-52-212-24-11.eu-west-1.compute.amazonaws.com:7180/api/v14/cm/version"
{
  "version" : "5.9.3",
  "buildUser" : "jenkins",
  "buildTimestamp" : "20170627-1506",
  "gitHash" : "23506bb4e114dd460bdac64c57a672e6be631907",
  "snapshot" : false
```
  * List all CM users
```
curl -u dboyer-ibm:cloudera "http://ec2-52-212-24-11.eu-west-1.compute.amazonaws.com:7180/api/v14/users"
{
  "items" : [ {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ]
  }, {
    "name" : "dboyer-ibm",
    "roles" : [ "ROLE_ADMIN" ]
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ]
  } ]
```
  * Report the database server in use by CM
```
curl -u dboyer-ibm:cloudera "http://ec2-52-212-24-11.eu-west-1.compute.amazonaws.com:7180/api/v14/cm/scmDbInfo"
{
  "scmDbType" : "MYSQL",
  "embeddedDbUsed" : false
}
```
