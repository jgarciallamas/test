Bootcamp JS for WP project

•	Overview
Accesing to the Ranch Systems online database through its JSON web service interface. All data access is secured by SSL and username/password authentication.
Note: I need to see how to tackle this since I don’t have any control over the server, so username/password should be coded in the URL, then I can’t make it public for security reasons.

The RS web services implementation is RESTful, it uses simple HTTP requests like GET and POST, I’m going to focus on GET requests though so that I can fetch and show the required information.

The process to get information would be as follow in the next example:
•	Get all properties that a particular user is authorized to access:
 
Will return something like:
 

•	Mandatory Parameters
uname --> User name
pword --> Password
reqtype --> Request type. This parameter specifies the request and further parameters may be required as per documentation below.

This is an example how the parameters must be set in the URL:
 

•	Request type “props”
Retrieves properties to which user has access.
No further parameters required.
Returns a JSON object with the following members:

 
Each property object has the following members:
 
•	Request type “propstat”
Retrieves status information about a particular property.
Requires the following additional URL parameters:
 
Returns a JSON object with the following members:
 
This is an example of what we get from this kind of request:
 
The important information here is the “healthindex” and “datatime” properties, since this gives us information about the unit health and the most recent data posted so that we can see if the unit is delayed for example.
The service level field is a number as follows:
 

•	Request type “rmsmap”
Retrieves a complete map (actually a tree) of all units and sensors in a property.
Requires the following additional URL parameters:
 

Returns a JSON object with the following members:
 
This is an example of what we get from this kind of request:
 
Each unit object has the following members:
 
The result would be similar to:
 
Each sensor object has the following members:
 
We would get something similar to this:
 

The idea would be 


