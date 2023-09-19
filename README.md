# PlatformEventFlow


// Create an instance of the Platform Event
Message_c__e event = new Message_c__e();

// Set the custom field value (e.g., "Create an Account" or "Create a Case")
event.action__c = 'CreateAccount';

// Publish the event
Database.SaveResult result = EventBus.publish(event);

// Check if the event was successfully published
if (result.isSuccess()) {
    System.debug('Event published successfully. Event ID: ' + result.getId());
} else {
    for (Database.Error error : result.getErrors()) {
        System.debug('Error while publishing event: ' + error.getMessage());
    }
}
