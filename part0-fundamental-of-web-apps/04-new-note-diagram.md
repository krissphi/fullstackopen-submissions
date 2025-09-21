sequenceDiagram
    participant browser
    participant server

    Note over browser: Write Notes & Click Save
    browser->>server: POST /exampleapp/new_note (body: note="...")
    activate server
    server-->>browser: 302 Redirect (Location: /exampleapp/notes)
    deactivate server

    Note right of browser: Browser mengikuti redirect
    browser->>server: GET /exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET /exampleapp/main.css
    activate server
    server-->>browser: CSS file
    deactivate server

    browser->>server: GET /exampleapp/main.js
    activate server
    server-->>browser: JavaScript file
    deactivate server

    Note right of browser: JS mulai jalan, minta data catatan
    browser->>server: GET /exampleapp/data.json
    activate server
    server-->>browser: JSON daftar catatan (termasuk yang baru)
    deactivate server

    Note right of browser: JS render ulang daftar <li> di halaman
