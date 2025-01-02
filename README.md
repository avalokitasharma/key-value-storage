# Key-Value Store

A lightweight key-value store implemented in Go, a simple client-server architecture. 
---

## Project Structure

```
key-value-store/
├── cmd/
│   ├── client/
│   │   └── main.go
│   ├── server/
│   │   └── main.go
├── internal/
│   ├── api/
│   │   ├── client_api.go
│   │   └── server_api.go
│   ├── service/
│   │   ├── client_service.go
│   │   └── server_service.go
│   ├── repo/
│   │   ├── storage.go
│   │   └── persistence.go
│   └── models/
│       └── kv_models.go
├── test/
│   ├── client_test.go
│   └── server_test.go
└── go.mod
```

---

## Features

- **Client-Server Architecture**: Separation of client and server logic for flexibility.
- **Persistence**: File-based persistent storage.
- **Thread-Safe Access**: Ensures concurrent access safety.
- **APIs**: Well-defined APIs for PUT, GET, and DELETE operations.
- **Simple to Use**: Easily start and interact with the server using the client.

---

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/avalokitasharma/key-value-storage.git
   cd key-value-store
   ```

2. Build the project:
   ```bash
   go build ./...
   ```

3. Run the server:
   ```bash
   go run cmd/server/main.go
   ```

4. Use the client to interact with the server:
   ```bash
   go run cmd/client/main.go
   ```

---

## API Documentation

### Client API

- `Put(key string, value string) error`
- `Get(key string) (string, error)`
- `Delete(key string) error`

### Server API

Handles incoming requests and delegates them to the service layer.
- POST `/put`: Adds a key-value pair.
- GET `/get?key=...`: Retrieves the value for a given key.
- DELETE `/delete?key=...`: Deletes a key-value pair.

---

## Example Usage

### Using Client Library

```go
package main

import (
    "fmt"
    "keyvaluestore/api"
)

func main() {
    client := api.NewClient("localhost:8080")

    err := client.Put("name", "GoLang")
    if err != nil {
        fmt.Println("Error:", err)
    }

    value, err := client.Get("name")
    if err != nil {
        fmt.Println("Error:", err)
    } else {
        fmt.Println("Value:", value)
    }
}
```

### Running Client and Server

1. Start the server:
   ```bash
   go run cmd/server/main.go
   ```

2. Run the client example:
   ```bash
   go run cmd/client/main.go
   ```

---

## Testing

Run the test cases to ensure everything works as expected:

```bash
go test ./test/...
```

---

## Incoming Improvements

- Add replication for high availability.
- Implement sharding for scalability.
- Include TLS/SSL for secure communication.
- Add an LRU cache for faster access.
- Provide containerized deployment with Docker.

---


## Contributing

Contributions are welcome! Please fork the repository and create a pull request with your changes.

