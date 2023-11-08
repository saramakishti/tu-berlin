## Second Meeting: 8 November 2023

In the UI:

- see the status of the entity (alive or not)
- every entity will register itself in the UI
- create a websocket with each entity (AP, C etc.) which is open all the time and pushes information
- get events from the websocket and interpret to visualize them
- config file that maps the numbers of the events with the name of the event [1 -> Attachment_Request_Sent]

An API call with React to get the 'existence' for the entities and then open the websocket

Websocket:

> ws:\\API\v1\

Entities:

- Access Point
- Client 1, 2 etc..
- Distirbuted Ledger Gateway

Entity:

- Name
- DID
- IP Address

Digital Wallet of an Entity:

- List of Verifiable Credentials (JSON Format)

Event:

- Group Name
- Message type name: msg_type: "1";
- Source DID: did:sov:test:1234567
- Target DID: did:sov:test:1234567
- Message: JSON

```
{
  group_name: "Attachment" | "1", //or numbers and convert to labels based on config [1 -> Attachment]
  message_type: "1",
  source_did: "did:sov:xxxx",
  target_did: "did:sov:xxx",
  message: {}
}
```

### Events (Message sent or received between entities)

1. Attachement

- 1: [Date, Time] Attachement Request Sent (Hi Bob - Alice)
- 2: Attachement Request Received (Bob Received)
  > (group between send and received, in a rectangle inside the sequence diagram)
- 3: Attachement Response Sent (Hi Alice - Bob)
- 4: Attachement Response Received (Alice Received)

2. Connection Setup

- Connection Request Sent
- Connection Request Received
- Connection Response Sent
- Connection Response Received

3. Presentation

- Request Sent
- Request Received
- Presentation Sent
- Presentation Received
- Presentation Acknowledged

4. DIDComm Messaging:

   **a. DID Resolution**

- DID Resolution Request Sent
- DID Resolution Request Received
- DID Resolution Response Sent
- DID Resolution Response Received

  **b. Service Registration**

- Service Registration Sent
- Service Registration Received
- Service Registration Successful Sent
- Service Registration Successful Received

  **c. Service Discovery**

- Service Discovery Sent
- Service Discovery Received
- Service Discovery Response Sent
- Service Discovery Response Received

  **d. Service Operation**

- Service Request Sent
- Service Received
- Service Response Sent
- Service Response Received

God's view

All entities and the sequence diagram that shows the connection between them

- use list as a filter for the sequence diagram

Entity specific views

- We see the roles of them, AP has the same role always
- AP is always the service repository role: like a log
- Views are specific to roles (AP has a list for all the services it provides from its network)
- offered, consumed, DLG view

Other Notes

- no button add entity, we get an entity event that populates the entity view list
- difference between a message type and message group we should "group" messages in the sequence diagram in a square box
- the gods view is a sequence diagram with a list of nodes that if clicked filter nodes out
- we have a node specific view that lists all services that are being offered and cosumed
- we need a database that saves all incoming messages and makes them available over a REST API
- repository view is a log of all registered services
- offered service list has an add button to add a new service
- topology view from demo will not be needed now
- demo created a database

### TODO:

- how the view can look like (sketches and demo)
- backend structure setup (important!)
- raw rendering of JSON - library I have used in a previous project (search it up)
- libraries to use (research)
