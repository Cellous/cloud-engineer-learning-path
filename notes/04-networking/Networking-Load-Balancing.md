## 2.3 Planning and Configuring Network Resources

### Key Concept
Google Cloud load balancers are selected based on:
- OSI layer
- internal vs external traffic
- regional vs global scope
- application traffic vs network traffic

### Important Rule
Application Load Balancer = Layer 7  
Network Load Balancer = Layer 4

### Diagnostic Lesson Learned
For secure web traffic using HTTP/HTTPS, choose an Application Load Balancer because it operates at Layer 7 and can route traffic using application-layer information such as headers, paths, and cookies.

### Official Documentation
- Cloud Load Balancing overview: [https://cloud.google.com/load-balancing/docs/load-balancing-overview]
- Networking Fundamentals
