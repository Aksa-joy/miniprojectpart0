sequenceDiagram
    participant browser
    participant server

    Note right of browser: The user writes a new note in the text field and clicks "Save"
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note right of server: The server saves the new note to the database
    server-->>browser: HTTP 201 Created (confirmation)
    deactivate server

    Note right of browser: The browser dynamically updates the list of notes
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... , { "content": "New Note", "date": "2025-1-21" }]
    deactivate server

    Note right of browser: The browser executes JavaScript to render the updated list of notes
    browser->>browser: Update the UI with the new note
