# Stripe Connections Tech Test
For this tech test, I will be implementing an Authorize, Capture and Cancel using the Stripe API. 

## Authorize()
An authorization request is the first method to execute when someone attempts to make an online payment using their card. The card needs to be checked for the following attributes:

- The card is active
- The card has sufficient funds
- The user is authorized to make a payment.

Once these have all been confirmed, Stripe will send a webhook event, `issuing_authorization.request`, to ask for a final confirmation.
As a user, you can either approve or decline the transaction.
If no activity is detected, Stripe will use your default settings to approve or decline the transaction.

### Method Design
The method must:
```
1. Read the Card Number
2. Check if the Card Number exists
3. Make a Request to determine how much funds are in the account
4. Confirm whether the funds are equal to or above the transaction amount
5. Request to determine if the user information matches the cardholder information
6. Send a webhook event, issuing_authorization.request
7. Wait for a response, if none, execute the default option
8. Return a successful authorization or an unsuccessful authorization
```