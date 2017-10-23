# Overview
The examples provided in this project are meant to illustrate how to use the TRACT 
Hosted Payment Iframe browser-based payment capture to meet your business needs.

The examples require an initial authenticated call to TRACT via a secure mechanism to retrieve a 
referrer token. This referrer token is short-lived and allows a developer to make calls against the TRACT Payment
service in a temporarily authenticated manner from a client browser.  This token can be used only
once to create a temporary payment method in TRACT.  A payment token is provided for this temporary payment
method which is then used to add a payment method to a billing account.

# Prerequisites 
* node.js is installed on your environment

    * See https://nodejs.org/en/download/
    * Tested with node version 8.6.0 

* Required node libraries are installed.

    * Navigate to /hosted-payment-iframe
    * Run `npm install`

* A TRACT tenant

    * goTransverse Customer Support will provide the domain name for your TRACT instance, (e.g. demo.tractbilling.com for the purposes of these examples)
    * goTransverse Customer Support will provide an api account for your TRACT tenant.
    
    
# Getting a Referrer Token

Using a tool like Postman, construct an HTTP post with the following information

```https://demo.tractbilling.com/t/s/r/1.33/payments/referrerToken```


## Request Headers

```Authorization: Basic <auth>``` 

```Content-Type: application/xml```
    
   Where `<auth>` is the base64 encoded <your-username>:<your-password>

    
## Request Body
```
<?xml version="1.0" encoding="UTF-8"?>
<generatePaymentCollectionReferrerToken xmlns="http://www.tractbilling.com/billing/1_33/domain">
    <errorUrl>http://www.yahoo.com?error</errorUrl>
    <cancelUrl>http://www.yahoo.com?cancel/</cancelUrl>
    <completeUrl>http://www.yahoo.com?complete/</completeUrl>
</generatePaymentCollectionReferrerToken>        
```

## Response Body
```        
<?xml version="1.0" encoding="UTF-8"?>
<referrer xmlns="http://www.tractbilling.com/billing/1_33/domain" referrerToken="d88f9360-e192-412e-8892-9f5adb24e844"/> 
```


# Iframe Name/Value Pairs Reference
You can input the fields in the table below into the iframe as name/value pairs.

| Field Name                      | Query Parameter Name         | Required | Description                                                                                                                                                                                                                           |
|---------------------------------|------------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| emailAddress                    | emailAddress                 | No       | The customer's email address.                                                                                                                                                                                                         |
| Card Type                       | cardType                     | Yes      | Choose one: AMEX, DISCOVER, MASTERCARD, VISA, DINERSCLUB. The credit card must be one of these types.                                                                                                                                 |
| Cardholder First Name           | cardholderFirstName          | No       | The first name of the person on the credit card.                                                                                                                                                                                      |
| Cardholder Middle Name          | cardholderMiddleName         | No       | The middle name of the person on the credit card.                                                                                                                                                                                     |
| Cardholder Last Name            | cardholderLastName           | Yes      | The last name of the person on the credit card. This parameter MUST be entered for any of the cardholder name fields to be injected.                                                                                                  |
| Cardholder Suffix               | cardholderSuffix             | No       | The suffix of the name, such as "III" or "Jr." of the person on the credit card.                                                                                                                                                      |
| Address Country Code            | addressCountryCode           | No       | The 3-digit ISO country code of the customer's address.                                                                                                                                                                               |
| Address Line 1                  | addressLine1                 | Yes      | The street address or postal address of the customer. This parameter MUST be entered for any of the address fields to be injected.                                                                                                    |
| Address Line 2                  | addressLine2                 | No       | Additional address information such as suite number.                                                                                                                                                                                  |
| Address City                    | addressCity                  | No       | The city of the customer's address.                                                                                                                                                                                                   |
| Address Region or State         | addressRegrionOrState        | No       | If the country is USA, Canada, or Mexico, then this field must be the 2-digit state, province, or region code of the Customer's address.                                                                                              |
| Address Postal Code             | addressPostalCode            | No       | The postal code or zip code for the customer's address.                                                                                                                                                                               |
| Phone Country Code              | phoneCountryCode             | No       | For the customer's phone number, the country code (1 to 3 digits). US and Canada are 1. ITU-T recommendations E.123 and E.164 are also called IDD International Direct Dialing (IDD) or International Subscriber Dialing (ISD) codes. |
| Phone National Destination Code | phoneNationalDestinationCode | No       | The area code for the customer's phone number.                                                                                                                                                                                        |
| Phone Subscriber Number         | phoneSubscriberNumber        | Yes      | The customer's phone number. This parameter MUST be entered for any of the phone fields to be injected.                                                                                                                               |
| Phone Extension                 | phoneExtension               | No       | The extension for the customer's phone number, if applicable.                                                                                                                                                                         |
