## New note in Single page app diagram

```mermaid
sequenceDiagram
participant Browser
participant Server
Browser->>Server: HTTP POST request to the address<br>new_note_spa bearing the user input
activate Server
Server-->>Browser: HTTP status code 201 created
deactivate Server
Note right of Browser: The page does not refresh and the browser<br> sends no further HTTP requests
```

* The POST request to the address `new_note_spa` contains the new note containing both the content of the note and the date
* The Server responds with status code `201 created`. The browser stays on the same page, and it sends no further HTTP requests.
