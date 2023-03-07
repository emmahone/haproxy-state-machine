# haproxy-state-machine

```mermaid
graph LR;
  A[Client] -->|1. SYN| B(HAProxy);
  B -->|2. SYN| C[Server1];
  B -->|3. SYN| D[Server2];
  C -->|4. SYN-ACK| B;
  D -->|5. SYN-ACK| B;
  B -->|6. ACK| A;
  A -->|7. HTTP Request| B;
  B -->|8. HTTP Request| C;
  C -->|9. HTTP Response| B;
  B -->|10. HTTP Response| A;
```

Explanation of the steps:

- The client sends a SYN packet to the HAProxy load balancer.
- The HAProxy load balancer forwards the SYN packet to Server1.
- The HAProxy load balancer forwards the SYN packet to Server2.
- Server1 responds with a SYN-ACK packet to the HAProxy load balancer.
- Server2 responds with a SYN-ACK packet to the HAProxy load balancer.
- The HAProxy load balancer responds with an ACK packet to the client, indicating that the connection has been established.
- The client sends an HTTP request to the HAProxy load balancer.
- The HAProxy load balancer forwards the HTTP request to Server1.
- Server1 responds with an HTTP response to the HAProxy load balancer.
- The HAProxy load balancer forwards the HTTP response to the client.
