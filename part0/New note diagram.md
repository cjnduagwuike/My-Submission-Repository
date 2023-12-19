 ## New note diagram

``` mermaid
sequenceDiagram
    participant Browser
    participant Server
    Browser->>Server: HTTP POST request to the server address new_note bearing<br> the user input
    activate Server
    Server-->> Browser: HTTP status code 302
    deactivate Server
    Note right of Browser: This is a URl redirect with which the server asks the browser<br> to do a new HTTP GET request
    Browser->>Server: HTTP GET request to the address notes
    Note right of Browser:This causes the browser to reload the page which in turn <br>causes three more HTTP GET requests fetching the stylesheet<br> (main.css), the Javascript file (main.js) and the raw data of <br>the notes (data.json)
    Browser->>Server:GET https://fullstack-exampleapp.herokuapp.com/main.css
    activate Server
    Server-->>Browser:CSS file
    deactivate Server
    Browser->>Server:GET https://fullstack-exampleapp.herokuapp.com/main.js
    activate Server
    Server-->>Browser:Javascript file
    deactivate Server
    Browser->>Server: GET https://fullstack-exampleapp.herokuapp.com/data.json
    activate Server
    Server-->>Browser: JSON files
    deactivate Server
```
<br>


* When the button on the form is clicked the browser will send the user input to the server
* It is an HTTP POST request to the server address new_note.
* The server responds with HTTP status code 302. This is a URL redirect, with which the server asks the browser to do a new a HTTP GET request to the address defined in the headers location - the address `notes`
* The browser reloads the page and this causes three more HTTP requests: fetching the CSS stylesheet (main.css), the Javascript file(main.js) and the raw data of the notes(data.json)

