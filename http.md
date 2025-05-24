## HTTP overview

### **Client-Server Model**
   - HTTP operates on a client-server model. The client (e.g., a web browser) sends a request to a server, and the server processes the request and sends back a response.

 **Stateless:**
 - By default, HTTP is a stateless protocol. This means each request from a client to a server is treated as an independent transaction. The server does not retain any information about previous requests from the same client.
 - *Note:* While HTTP itself is stateless, stateful sessions are often managed using techniques like cookies, server-side sessions, or tokens (e.g., JWT).

### Connectionless (Historically, with caveats)
- **HTTP/1.0:** Was truly connectionless. For each request/response pair, a new TCP connection was established and then closed.
- **HTTP/1.1:** Introduced persistent connections (keep-alive). The TCP connection can be reused for multiple requests/responses, reducing latency.
- **HTTP/2 & HTTP/3:** Further optimize connections with multiplexing over a single TCP connection (HTTP/2) or QUIC (HTTP/3), allowing multiple requests and responses to be sent/received concurrently.

### Resource Identification (URIs/URLs)
- HTTP uses Uniform Resource Identifiers (URIs), most commonly Uniform Resource Locators (URLs), to identify resources on the web (e.g., HTML files, images, APIs).
- The components of a URL are:
	1. Scheme/Protocol
	2. Subdomain
	3. Domain name
	4. Top-level domain
	5. Port
	6. Path
	7. Query parameters
	8. Fragment

`https://blog.example.com:443/post/2023/web-dev?id=123&sort=asc#comments`

 ### HTTP Methods 
-    These define the action to be performed on a resource. Common methods include:
	- **GET:** Retrieves a representation of a resource.
	- **POST:** Submits data to be processed to a specified resource (e.g., form submission, creating a new resource).
	- **PUT:** Replaces all current representations of the target resource with the request payload.
	- **DELETE:** Deletes the specified resource.
	- **PATCH:** Applies partial modifications to a resource.
	- **HEAD:** GET without the response body (useful for checking metadata).
	- **OPTIONS:** Describes the communication options for the target resource. Used for preflight requests
	- **CONNECT:** Establishes a tunnel to the server identified by the target resource.
	- **TRACE:** Performs a message loop-back test along the path to the target resource.

### HTTP Headers
- These provide metadata about the HTTP request or response. They are key-value pairs and control various aspects of the communication, such as:
- **Content Negotiation:** (e.g., `Accept`, `Accept-Language`, `Content-Type`) Allows the client and server to agree on the format and characteristics of the resource being exchanged.
- **Caching:** (e.g., `Cache-Control`, `ETag`, `Last-Modified`) Enables efficient caching mechanisms to reduce server load and latency.
- **Authentication:** (e.g., `Authorization`, `WWW-Authenticate`) Provides mechanisms for client authentication.
- **Cookies:** (e.g., `Set-Cookie`, `Cookie`) Used for session management and tracking user state.
- **Redirection:** (e.g., `Location`) Directs the client to a different URL.
- **Message Body Information:** (e.g., `Content-Length`, `Content-Encoding`) Describes the payload.

### Status Codes
- The server's response includes a 3-digit status code indicating the outcome of the request. These are grouped into categories:
	- **1xx (Informational):** Request received, continuing process.
	- **2xx (Successful):** The action was successfully received, understood, and accepted (e.g., `200 OK`, `201 Created`).
	- **3xx (Redirection):** Further action needs to be taken by the user agent to fulfill the request (e.g., `301 Moved Permanently`, `302 Found`).
	- **4xx (Client Error):** The request contains bad syntax or cannot be fulfilled (e.g., `400 Bad Request`, `401 Unauthorized`, `404 Not Found`).
	- **5xx (Server Error):** The server failed to fulfill an apparently valid request (e.g., `500 Internal Server Error`, `503 Service Unavailable`).

8.  Message Body (Payload)
-  Requests (like POST, PUT) and responses can optionally carry a message body containing the actual data being transferred (e.g., HTML content, JSON data, image files).

8. Security (via HTTPS)
    - While HTTP itself is not secure (transmits data in plain text), **HTTPS (HTTP Secure)** layers HTTP over TLS/SSL (Transport Layer Security/Secure Sockets Layer) to provide:
        *   **Encryption:** Protects data from eavesdropping.
        *   **Authentication:** Verifies the identity of the server (and optionally the client).
        *   **Integrity:** Ensures data has not been tampered with during transit.

## How does HTTPS work?
HTTPS (Hypertext Transfer Protocol Secure) enables encrypted traffic by combining the standard HTTP protocol with a security layer, primarily **TLS (Transport Layer Security)**, which is the successor to SSL (Secure Sockets Layer).

Here's a simplified breakdown of how it works:

1.  **Initiation of Secure Connection:**
    *   When you type `https://` in your browser, the browser (client) attempts to establish a secure connection with the server on port 443 (default for HTTPS).

2.  **TLS Handshake (The Core Process):** This is where the magic happens, involving both **asymmetric (public/private key)** and **symmetric (shared secret key)** encryption.

    *   **Client Hello:** Your browser sends a "Client Hello" message to the server, listing the TLS versions it supports, the cipher suites (encryption algorithms) it prefers, and a random number.
    *   **Server Hello & Certificate:** The server responds with a "Server Hello," choosing the best TLS version and cipher suite from the client's list. Crucially, it also sends its **SSL/TLS certificate** (an X.509 certificate). This certificate contains the server's public key, its domain name, expiration date, and is digitally signed by a trusted **Certificate Authority (CA)**.
    *   **Certificate Validation:** Your browser then validates the server's certificate:
        *   It checks if the certificate is issued by a CA it trusts (most browsers have a pre-installed list of trusted CAs).
        *   It verifies the certificate's expiry date.
        *   It checks if the domain name in the certificate matches the website's domain name.
        *   It verifies the certificate's digital signature to ensure it hasn't been tampered with.
        *   If any of these checks fail, the browser warns you about an insecure connection.
    *   **Key Exchange:**
        *   The browser generates a **pre-master secret** (a random value).
        *   It encrypts this pre-master secret using the server's **public key** (from the certificate).
        *   It sends the encrypted pre-master secret to the server.
        *   Only the server, possessing the corresponding **private key**, can decrypt this pre-master secret.
        *   Both the client and server then independently derive a **master secret** and subsequent **session keys** from this pre-master secret and the random numbers exchanged earlier. These session keys will be used for symmetric encryption.
    *   **Handshake Completion:** Both sides send "Finished" messages, encrypted with the newly derived session key, to confirm they are ready to proceed with encrypted communication.

3.  **Encrypted Data Transfer (Symmetric Encryption):**
    *   Once the TLS handshake is complete, all subsequent HTTP data (requests, responses, cookies, form data, etc.) is encrypted using the agreed-upon **symmetric session keys**. Symmetric encryption is much faster for bulk data transfer than asymmetric encryption.
    *   Each message is also authenticated using a Message Authentication Code (MAC) to ensure its **integrity** (that it hasn't been tampered with) and **authenticity** (that it came from the expected sender).

**In Summary:**

HTTPS enables encrypted traffic by using **TLS** to perform a secure handshake. This handshake leverages **asymmetric encryption (public/private keys)** to securely exchange a shared **symmetric key**. Once the shared symmetric key is established, all subsequent communication is encrypted using this faster **symmetric encryption**. This process provides three critical security features:

*   **Confidentiality:** Data is encrypted, so only the intended recipient can read it.
*   **Integrity:** Data cannot be modified without detection.
*   **Authentication:** You can be sure you're communicating with the legitimate server, not an impostor.
