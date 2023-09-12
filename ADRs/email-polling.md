# ADR.2 E-mail Polling
This ADR describes the approach to E-mail polling and processing which are crucial processes for collecting 
travel-related events such as itinerary receipts, hotel bookings, etc.

## Status `PROPOSED`

## Rationale
In order to process E-mails, the Road Warrior should be provided with read-only access to the user's mailbox. However,
we should not require users to give their credential to the Road Warrior directly. That would be considered by majority 
of users as a privacy violation and a big security threat. Besides, there are mail servers protected by 2FA, private
mail servers that require VPN connection, hence the credentials would not work. Beyond credentials (username and 
password) a connection to a mail server requires some technical information to be provided such as server address, 
protocol (POP/IMAP), various ports, TLS parameters. This often the information an end user is not aware of and 
therefore users will not use the app due to the inability to correctly configure the app.

There are ways however to provide access to mailbox indirectly:

1. **Connect Mailbox** (server side): Works with mail platforms allowing token-based access for 3<sup>rd</sup> party 
   applications after owner's approval; particularly, Gmail. From the user's point of view this looks like a button 
   that redirects to service provider's page allowing to grant or deny the access.
    
2. **Use Mailbox** (client side): The mobile app acts as an E-mail client, accessing mailbox configuration and 
credentials from the system (iOS, Android) Internet Accounts registry. User just need to select a mailbox to use
in the app settings or initial set-up wizard.

The second approach looks more beneficial since the E-mails processed locally on device, and only those related to 
travel will be sent to the back end; local device network settings are used (including VPN) so private mail servers
can be accessed.

## Decision
Combine both approaches for maximum coverage of possible mail server configurations and user behavioral patterns. 

## Consequences

Positive:

* Security and privacy is respected since users grant access to the app without compromising credentials.

Negative:

* Users who do not grant access to their mailbox will have poor experience using the app (almost useless).