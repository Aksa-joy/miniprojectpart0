sequenceDiagram
    participant browser
    participant server

    Note right of browser: The user writes a note in the text field and clicks "Save"
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    Note right of server: The server receives the note content and saves it to the database
    server-->>browser: HTTP 201 Created
    deactivate server

    Note right of browser: The browser executes JavaScript to update the UI
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function to render the updated list of notes
    browser->>browser: Update the UI with the new note
