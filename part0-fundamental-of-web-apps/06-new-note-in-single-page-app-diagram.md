sequenceDiagram
    participant browser
    participant server

    Note over browser: User isi form & submit
    Note right of browser: JS intercept (e.preventDefault())

    Note right of browser: JS push note ke memori & render langsung ke layar
    browser->>server: POST /exampleapp/new_note_spa
    activate server
    Note left of server: Header: Content-Type: application/json
    Note left of server: Body: {"content":"...", "date":"..."}
    server-->>browser: 201 Created (OK)
    deactivate server

    Note right of browser: Tidak ada redirect. Halaman tetap.
