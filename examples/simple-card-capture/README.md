# Instructions

1. Navigate to /hosted-payment-iframe/examples/simple-card-capture folder. Use your-tract-domain as a parameter in the following command.
    * Run `node app.js demo.tractbilling.com`
    
2. Retrieve a referrer token from the TRACT API. (See top level README.md file for more information.)        

3. Navigate to test page
    * http://localhost:1111/index.html?t=d88f9360-e192-412e-8892-9f5adb24e844

4. Fill out sample data.  Note that this data is only used to inject into the hosted payment page IFRAME.  You should gather
this information in a manner suitable for your checkout flow.
    * Use Visa Card 4111111111111111 with current or future expiration date
    * Enter any address information
    * Hit Submit button

5. Receive successful response URL with payment method refrence token in URL
    * e.g. http://localhost:1111/success.html?r=c0294abb-4ca6-4b8b-99c9-3541e5654345
    
This received token can then be used to add this payment method to a billing account later in the flow.

# TENANT Configuration Options for HPP

1. If you want to override the CSS, you must go to Admin -->  Company --> Branding --> Action (Configure Secure Payment Collection Branding)
* Enable and upload your override CSS.  See example_override.css as an example.

2. If you want CVV to show in page, set "Allow Payment CVV" to true in Admin --> Company --> System Settings

3. If you want Cancel and Next buttons to display, you need to pass in valid values for cancel and success in the original referrer token generation.


# IFrame Name/Value Pairs Reference
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
