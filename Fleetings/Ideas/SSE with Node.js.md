---
tags:
  - type/sketchnote
  - type/note
aliases: 
lead: +++ Lead paragraph goes here +++
visual: "![[image.jpg]]"
created: 2025-04-18, 22:49
modified: 2025-04-18, 22:49
template_type: Note
template_version: "1.35"
license: © 2022-2025 by Edmund Gröpl under CC BY-NC-SA 4.0
updated: 2025-04-19T20:39
---
<!--  See "Template Help" below for using properties -->

# SSE with Node.js
<!--  Clear and descriptive title -->

<!-- My sketchnote if available -->
```dataviewjs 
dv.paragraph(dv.current().visual);
```
<small>_Zoom: [[]] | Edit: [[]]_</small>

<!--  Most essential idea from "lead"-key  in properties section -->

> [!Summary]
> `= this.lead`

**Details**
# SSE Example in Node.js

Let’s dive into the implementation and see how you can create a simple SSE server in Node.js and listen for updates on the client side.

## Step 1: Set Up the Node.js Server

We’ll start by creating a basic Node.js server that streams events to the client. The `express` library can be used to handle routing, but SSE can also be implemented using native HTTP modules.

```

const express = require("express");
const cors = require("cors");
const app = express();

// Enable CORS for all routes

app.use(
  cors({
    origin: "*", // In production, you should specify the exact origin
    methods: "GET,HEAD,PUT,PATCH,POST,DELETE",
    credentials: true,
    optionsSuccessStatus: 204,
  })
); 
  
app.get('/events', (req, res) => {  
// Set headers to keep the connection alive and tell the client we're sending event-stream data  
res.setHeader('Content-Type', 'text/event-stream');  
res.setHeader('Cache-Control', 'no-cache');  
  
// Send an initial message  
res.write(`data: Connected to server\n\n`);  
  
// Simulate sending updates from the server  
let counter = 0;  
const intervalId = setInterval(() => {  
counter++;  
// Write the event stream format  
res.write(`data: Message ${counter}\n\n`);  
}, 2000);  
  
// When client closes connection, stop sending events  
req.on('close', () => {  
clearInterval(intervalId);  
res.end();  
});  
});  
  
app.listen(3000, () => {  
console.log('SSE server started on port 3000');  
});

```

## Step 2: Create the Client-Side HTML

Now, let’s create a simple HTML file to receive and display these events.

```

<!DOCTYPE html>  
<html lang="en">  
<head>  
<meta charset="UTF-8">  
<meta name="viewport" content="width=device-width, initial-scale=1.0">  
<title>SSE Example</title>  
</head>  
<body>  
<h1>Server-Sent Events</h1>  
<ul id="events"></ul>  
  
<script>  
// Initialize the EventSource, listening for server updates  
const eventSource = new EventSource('http://localhost:3000/events');  
  
// Listen for messages from the server  
eventSource.onmessage = function(event) {  
const newElement = document.createElement("li");  
newElement.textContent = event.data;  
document.getElementById("events").appendChild(newElement);  
};  
  
// Log connection error  
eventSource.onerror = function(event) {  
console.log('Error occurred:', event);  
};  
</script>  
</body>  
</html>

```

- The `EventSource` API in the browser is used to connect to the SSE endpoint.
- The `onmessage` handler listens for messages from the server and appends them to an HTML list (`<ul>`).
- The browser automatically manages reconnections if the connection drops.

## Step 3: Running the Application

1. Install the necessary package:

```
npm install express, cors
```


2. Run your server:

```
node app.js
```

3. Open the HTML file in your browser and see the server’s live updates being displayed.

# Advanced Features of SSE

## 1. Custom Events

SSE supports custom event types. Instead of the default `onmessage`, you can define specific event handlers on the client side. For example:

**Server-side (sending a custom event)**:

res.write(`event: customEvent\n`);  
res.write(`data: This is a custom event message\n\n`);

**Client-side (listening for the custom event)**:

eventSource.addEventListener('customEvent', function(event) {  
    console.log('Custom event received:', event.data);  
});

## 2. Reconnection and Last-Event-ID

SSE automatically reconnects if the connection drops. The `Last-Event-ID` header can be used to ensure the client receives missed messages after reconnection. This is useful for ensuring data integrity during temporary connection losses.

**Server-side (sending an event with an ID)**:

res.write(`id: 123\n`);  
res.write(`data: Message with ID 123\n\n`);

**Client-side (managing reconnection)**: The browser automatically sends the `Last-Event-ID` header during reconnection, and the server can use this to resume from the last message ID.

# Conclusion

Server-Sent Events (SSE) offer a simple, lightweight, and efficient way to stream real-time updates from the server to the client using standard HTTP. They are ideal for applications where the client only needs to receive updates, such as live feeds, notifications, or real-time dashboards.

With automatic reconnection and cross-browser support, SSE provides a robust and developer-friendly solution for many real-time data streaming use cases. While WebSockets may be the right choice for two-way communication, SSE shines in scenarios where unidirectional communication from server to client is needed.

## 내 생각

keep-alive는 http2사양에서 금지라고했는데?

**Supporting Content**
<!-- Supporting content in tail of my note  -->
- 

---
# Back Matter

**Source**
<!-- Always keep a link to the source- --> 
- based_on::

**References**
<!-- Links to pages not referenced in the content. see: [[related note]] because <reason> -->
- see:: 

**Terms**
<!-- Links to definition pages. -->
- 

**Target**
<!-- Link to project note or externaly published content. -->
- used_in::

---
**Tasks**
<!-- What remains to be done with this note? --> 
- 

**Questions**
<!-- What remains for you to consider? --> 
- question::

---
**Template Help**
<!-- Links to external help pages on GitHub. -->
- [Basic Template Structure](https://github.com/groepl/Obsidian-Templates#basic-template-structure)
- [How to Use Links](https://github.com/groepl/Obsidian-Templates#how-to-use-links)
- [How to Use Tags](https://github.com/groepl/Obsidian-Templates#how-to-use-tags)
- [How to Search Notes](https://github.com/groepl/Obsidian-Templates#how-to-search-notes)
- [Plugins Needed](https://github.com/groepl/Obsidian-Templates#obsidian-plugins-needed)
- [Find Latest Updates](https://github.com/groepl/Obsidian-Templates)