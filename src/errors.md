# Errors

<aside class="notice">
Please note that there error/success codes are split into two sections based on intended and not normal behavior.
</aside>

The aspace API uses the following error codes to indicate behavior that isn't normal:

Error Code | Meaning | HTTP Code
---------- | ------- | ---------
4 | <b>Invalid PIN</b> - The PIN given doesn't match the one sent during the authentication process. | 200
12 | <b>Invalid Phone</b> - The phone given is not valid. | 200
13 | <b>Invalid Auth Key</b> - The authority key to complete the following request is not valid. | 403
15 | <b>Invalid Spot ID</b> - The parking spot id given doesn't exist within the database.
16 | <b>Invalid Basic Authentication</b> - The credentials given for the method's basic authentication are invalid. | 401
20 | <b>Missing Body</b> - The request requires a body, but one was not sent with the request. | 422
21 | <b>Invalid Occupancy Status</b> - An invalid occupancy status was given as part of the request. Only "T", "F", and "N" are allowed. | 422
23 | <b>PIN Expired</b> - An expired PIN was sent as part of the request during the authentication. A new PIN must be requested and used. | 403
24 | <b>Invalid Spot ID</b> - No parking spots exist with the given Spot ID exist in the database. | 404
25 | <b>Invalid Spot or Block ID</b> - No parking spots exist with both the given Spot and Block IDs in the database. | 404
26 | <b>Invalid Permission</b> - The permission that you requested or used is not a registered/valid permission. | 200
39 | <b>Invalid Vehicle ID</b> - The vehicle ID you are attempting to remove doesn't exist. | 200

The aspace API uses the following error codes to indicate requests that are made with invalid/incomplete parameters:

Error Code | Meaning | HTTP Code
---------- | ------- | ---------
-1 | <b>Missing Parameter</b> - Your request is missing a parameter, specified in the info part of the return body. | 422
-2 | <b>Invalid Access Code</b> - Your request is attempting to use an invalid access_code/device_id combination. | 200
-3 | <b>Expired Access Code</b> - Your request is attempting to use an expired access_code/device_id combination. | 200
-5 | <b>Multi-Part Body Missing</b> - The endpoint method you are calling requires a multi-part body with a key that is missing from your request. | 422
-7 | <b>Invalid or Missing Output Type</b> - The endpoint method you are calling requires an output type as part of its request to function, and one wasn't found or wasn't provided. | 422

The aspace API uses the following success codes to indicate behavior that is intended:

Success Code | Meaning | HTTP Code
------------ | ------- | ---------
1 | <b>New Phone</b> - The phone number used in the authentication doesn't have an existing account. | 200
2 | <b>Returning Phone</b> - The phone number used in the initial authentication has an existing account. | 200
17 | <b>Authority Key Added</b> - The authority key and requested permissions were successfully added. | 200
19 | <b>Spot Status Changed</b> - The given spot_id's status was successfully changed to the given occupancy status. | 200
22 | <b>New Access Code</b> - A new access code was issued for the user at the end of the authentication process. | 200
30 | <b>Main Endpoint Function Success</b> - The Main endpoint is functioning as intended. | 200
31 | <b>Routing Endpoint Function Success</b> - The Routing endpoint is functioning as intended. | 200
32 | <b>Admin Endpoint Function Success</b> - The Admin endpoint is functioning as intended. | 200
33 | <b>Auth Endpoint Function Success</b> - The Auth endpoint is functioning as intended. | 200
34 | <b>Parking Endpoint Function Success</b> - The Parking endpoint is functioning as intended. | 200
35 | <b>User Endpoint Function Success</b> - The User endpoint is functioning as intended. | 200
36 | <b>Profile Pic Exists</b> - The profile picture of the user matching the access_code and device_id given exists at a given URL. | 200
37 | <b>Profile Pic Null</b> - The profile picture of the user matching the access_code and device_id doesn't exist and/or has never been updated. | 200
38 | <b>Profile Pic Updated</b> - The profile picture of the user matching the access_code and device_id has been successfully updated. | 200
