sequenceDiagram
    participant browser
    participant server

    browser->>server: GET /exampleapp/spa
    activate server
    server-->>browser: HTML (form tanpa action/method)
    deactivate server

    browser->>server: GET /exampleapp/main.css
    activate server
    server-->>browser: CSS file
    deactivate server

    browser->>server: GET /exampleapp/spa.js
    activate server
    server-->>browser: JavaScript (SPA)
    deactivate server

    Note right of browser: JS berjalan, ambil data catatan
    browser->>server: GET /exampleapp/data.json
    activate server
    server-->>browser: JSON daftar catatan
    deactivate server

    Note right of browser: JS render daftar catatan ke DOM (tanpa reload)
