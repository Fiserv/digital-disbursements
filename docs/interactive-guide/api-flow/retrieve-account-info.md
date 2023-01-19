## Step 4a: Retrieve Account Info (Optional/Informative)

### Description
This request will retrieve the account information based on the `recipientId`. This will return **ALL** associated payment methods with this `recipientId`. Remember the `recipientId` changes based upon email so if multiple `merchantCustomerIds` share the same email this will pull all the accounts from every `merchantCustomerId` associated with that email.