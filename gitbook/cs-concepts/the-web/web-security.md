# Web Security

## Browser Security Model

JavaScript is executed in a sandbox withing wich the following actions are *not* permitted:
- Start new processes or access other existing processes. 
- Read arbitrary chunks of system memory. As a managed memory language, JavaScript can’t read memory outside its sandbox.
- Access the local disk. Modern browsers allow websites to store small amounts of data locally, but this storage is abstracted from the filesystem itself. 
- Access the operating system’s network layer. 
- Call operating system functions.

JavaScript executing in the browser sandbox is permitted to do the following actions:
- Read and manipulate the DOM of the current web page. 
- Listen to and respond to user actions on the current page by registering event listeners.
- Make HTTP calls on behalf of the user.
- Open new web pages or refresh the URL of the current page, but only in response to a user action. 
- Write new entries to the browser history and go backward and forward in history.
- Ask for the user’s location.
- Ask permission to send desktop notifications.

## Further Reading
[Web Security for Developers](https://nostarch.com/websecurity)
