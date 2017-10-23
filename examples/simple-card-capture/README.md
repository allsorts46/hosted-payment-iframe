# Instructions

1. Run application from /hosted-payment-iframe/examples/simple-card-capture folder with <your-tract-domain> as parameter
    * node app.js foo.tractbilling.com
    
2. Retrieve a referrer token from the TRACT API

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
* Enable and upload your override CSS.  See example_override.css as and example.

2. If you want CVV to show in page, set "Allow Payment CVV" to true in Admin --> Company --> System Settings
