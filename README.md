# A checklist for creating a generic website

Here is a checklist for creating a full-fledged website.
I use HTML, CSS, Go.

## 1. Pre-requisites

- [ ] `go version`: Check progrmaming language version
- [ ] `curl` tool
- [ ] Web browser
- [ ] IDE

## 2. Foundations

- [ ] Set up project and create module
  - [ ] `go mod init <module_name>`
  - [ ] `touch main.go`
  - [ ] Ensure `Hello World` program works.
- [ ] Implement web application basics
  - [ ] Implement a `handler`: [`http.NewServeMux`](https://pkg.go.dev/net/http#NewServeMux)
  - [ ] Implement a `router` / `request multiplexer`: [`type ServeMux`](https://pkg.go.dev/net/http#ServeMux)
  - [ ] Implement a `web server`: [`func ListenAndServe`](https://pkg.go.dev/net/http#ListenAndServe)
- [ ] Configure routing requests
  - [ ] Add new `GET` routes: `about`, `contact`, ...
  - [ ] Restrict subtree path routing with `{$}`
- [ ] Define wildcard route patterns
- [ ] Implement method-based routing
  - [ ] Prefix the route pattern with the necessary HTTP method when declaring it: GET, POST, ...
  - [ ] Test: `curl --head localhost:4000/` & `curl -i -d "" localhost:4000/`
- [ ] Customize responses
  - [ ] Customize HTTP status codes with [status codes constants](https://pkg.go.dev/net/http#pkg-constants)
  - [ ] Customize headers
  - [ ] Write response bodies: [io.Writer](https://pkg.go.dev/io#Writer)
- [ ] Organize project structure
  - [ ] `mkdir -p cmd/web internal ui/html ui/static`
    - [ ] `cmd`: application-specific code for the executable applications in the project
    - [ ] `internal`: ancillary non-application-specific code used in the project
    - [ ] `ui`: user-interface assets used by the web application
  - [ ] `touch cmd/web/main.go`: Add code related to `func main()`
  - [ ] `touch cmd/web/handlers.go`: Add router code related to `func home()`, `func about()`, `func contact()`, ...
- [ ] Create HTML templates and inheritance

  - [ ] `mkdir ui/html/pages`
  - [ ] Add `home.html` page
  - [ ] Use: [`template.ParseFiles`](https://pkg.go.dev/html/template#ParseFiles) in `handlers.go`
  - [ ] Template composition base file: `touch ui/html/base.html`
    - [ ] Add content for `base.html`
    - [ ] Update `home.html`
    - [ ] Update `handler.go` file to jointly parse both files.
    - [ ] Update `ExecuteTemplate`
  - [ ] Embed partials:
    - [ ] `mkdir ui/html/partials`
    - [ ] `touch ui/html/partials/nav.tmpl`

- [ ] Set up serving of static files
- [ ] Implement http.Handler interface

## 3. Configuration and Error Handling

- [ ] Manage configuration settings
- [ ] Implement structured logging
- [ ] Set up dependency injection
- [ ] Create centralized error handling
- [ ] Isolate application routes

## 4. Database-Driven Responses

- [ ] Set up MySQL
- [ ] Install database driver
- [ ] Configure modules and reproducible builds
- [ ] Create database connection pool
- [ ] Design database model
- [ ] Write SQL statements
- [ ] Implement single-record SQL queries
- [ ] Implement multiple-record SQL queries
- [ ] Handle transactions and other details

## 5. Dynamic HTML Templates

- [ ] Display dynamic data
- [ ] Implement template actions and functions
- [ ] Set up caching for templates
- [ ] Handle runtime errors
- [ ] Implement common dynamic data handling
- [ ] Create custom template functions

## 6. Middleware

- [ ] Understand how middleware works
- [ ] Set common headers
- [ ] Implement request logging
- [ ] Create panic recovery system
- [ ] Design composable middleware chains

## 7. Processing Forms

- [ ] Set up HTML form
- [ ] Parse form data
- [ ] Validate form data
- [ ] Display errors and repopulate fields
- [ ] Create validation helpers
- [ ] Implement automatic form parsing

## 8. Stateful HTTP

- [ ] Choose session manager
- [ ] Set up session manager
- [ ] Implement working with session data

## 9. Server and Security Improvements

- [ ] Configure http.Server struct
- [ ] Set up server error log
- [ ] Generate self-signed TLS certificate
- [ ] Run HTTPS server
- [ ] Configure HTTPS settings
- [ ] Implement connection timeouts

## 10. User Authentication

- [ ] Set up authentication routes
- [ ] Create users model
- [ ] Implement user signup and password encryption
- [ ] Create user login functionality
- [ ] Implement user logout
- [ ] Set up user authorization
- [ ] Implement CSRF protection

## 11. Using Request Context

- [ ] Understand how request context works
- [ ] Implement request context for authentication/authorization

## 12. File Embedding

- [ ] Embed static files
- [ ] Embed HTML templates

## 13. Testing

- [ ] Write unit tests and sub-tests
- [ ] Test HTTP handlers and middleware
- [ ] Perform end-to-end testing
- [ ] Customize test running
- [ ] Mock dependencies
- [ ] Test HTML forms
- [ ] Conduct integration testing
- [ ] Profile test coverage
