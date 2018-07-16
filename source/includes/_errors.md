# Errors

<aside class="notice">
Please note that there error/success codes are split into two sections based on intended and not normal behavior.
</aside>

The aspace API uses the following custom error codes indicating behavior that isn't normal:

Error Code | Meaning | HTTP Code
---------- | ------- | ---------
-1 | Missing Parameter - Your request is missing a parameter, specified in the info part of the return body. | 422
4 | Invalid Pin - The pin given doesn't match the one sent during the authentication process. | 200
5 | Database Error - An error occurred on the backend during the query resulting in an error. | 500
12 | Invalid Phone - The phone given is not valid. | 200
13 | Invalid Auth Key - The authority key to complete the following request is not valid. | 403
14 | Missing Auth Key - The request requires an authority key, but one was never sent as part of the request. | 401
15 | Invalid Spot ID - The parking spot id given doesn't exist within the database.
16 | Invalid Basic Authentication - The credentials given for the method's basic authentication are invalid. | 401
18 | Authority Key Not Added - The authority key and requested permissions were not successfully added due to an unauthorized permission. | 403
20 | Missing Body - The request requires a body, but one was not sent with the request. | 422
21 | Invalid Occupancy Status - An invalid occupancy status was given as part of the request. Only "T", "F", and "N" are allowed. | 422
23 | Pin expired - An expired PIN was sent as part of the request during the authentication. A new PIN must be requested and used. | 403
24 | Invalid Spot ID - No parking spots exist with the given Spot ID exist in the database. | 404
25 | Invalid Spot or Block ID - No parking spots exist with both the given Spot and Block IDs in the database. | 404
26 | Invalid Permission - The permission that you requested or used is not a registered/valid permission. | 200

The aspace API uses the following custom success codes indicating behavior that is intended:

Success Code | Meaning | HTTP Code
------------ | ------- | ---------
1 | New Phone - The phone number used in the authentication doesn't have an existing account. | 200
2 | Returning Phone - The phone number used in the initial authentication has an existing account. | 200
17 | Authority Key Added - The authority key and requested permissions were successfully added. | 200
19 | Spot Status Changed - The given spot_id's status was successfully changed to the given occupancy status. | 200
22 | New Access Code - A new access code was issued for the user at the end of the authentication process. | 200