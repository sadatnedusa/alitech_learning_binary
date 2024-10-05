# Message Passing
---
## **Message Passing** is a method of inter-process communication (IPC) that allows processes to communicate and synchronize their actions by sending and receiving messages. Unlike shared memory, where processes can read and write to a common memory space, message passing involves sending data as discrete packets (messages) between processes. This model is widely used in distributed systems, microservices, and concurrent programming.

### Key Features of Message Passing

1. **Encapsulation**: Each message encapsulates data and metadata (such as the sender's identity), allowing for structured communication between processes.
  
2. **Asynchronous and Synchronous Communication**:
   - **Synchronous**: The sending process waits until the message is received by the receiving process. This can lead to blocking behavior.
   - **Asynchronous**: The sending process sends the message and continues its execution without waiting for the receiver to acknowledge receipt.

3. **Decoupling**: Message passing decouples the sender and receiver, allowing them to operate independently. This is particularly useful in distributed systems where processes may not be running on the same machine.

4. **Reliability**: Depending on the implementation, message passing can ensure that messages are delivered reliably, even in the presence of failures.

### Message Passing in Linux

In Linux, message passing is typically implemented using **message queues** or **sockets**. Here’s a detailed look at each:

#### 1. Message Queues

- **Description**: Message queues allow processes to send and receive messages in a queue format. Messages can be prioritized and stored until they are retrieved.

- **Creating a Message Queue**: Use the `msgget()` function to create or access a message queue.

- **Sending Messages**: Use the `msgsnd()` function to send messages to the queue.

- **Receiving Messages**: Use the `msgrcv()` function to retrieve messages from the queue.

- **Example**:

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <sys/ipc.h>
#include <sys/msg.h>

struct msg {
    long msg_type;
    char text[100];
};

int main() {
    key_t key = ftok("progfile", 65);  // Generate a unique key
    int msgid = msgget(key, 0666 | IPC_CREAT); // Create a message queue

    struct msg message;
    message.msg_type = 1; // Message type
    strcpy(message.text, "Hello from Message Queue!");

    // Send message
    msgsnd(msgid, &message, sizeof(message), 0);
    printf("Message sent: %s\n", message.text);

    // Receive message
    msgrcv(msgid, &message, sizeof(message), 1, 0);
    printf("Message received: %s\n", message.text);

    // Destroy the message queue
    msgctl(msgid, IPC_RMID, NULL);

    return 0;
}
```

#### 2. Sockets

- **Description**: Sockets provide a communication endpoint for message passing, enabling processes to communicate over a network or locally. They can support both stream (TCP) and datagram (UDP) communication.

- **Example**:

  - **Server Code**:

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <arpa/inet.h>

int main() {
    int server_fd, new_socket;
    struct sockaddr_in address;
    int opt = 1;
    int addrlen = sizeof(address);
    char buffer[1024] = {0};

    // Create socket file descriptor
    server_fd = socket(AF_INET, SOCK_STREAM, 0);
    setsockopt(server_fd, SOL_SOCKET, SO_REUSEADDR, &opt, sizeof(opt));

    address.sin_family = AF_INET;
    address.sin_addr.s_addr = INADDR_ANY;
    address.sin_port = htons(8080);

    // Bind
    bind(server_fd, (struct sockaddr *)&address, sizeof(address));

    // Listen
    listen(server_fd, 3);

    // Accept
    new_socket = accept(server_fd, (struct sockaddr *)&address, (socklen_t*)&addrlen);
    read(new_socket, buffer, 1024);
    printf("Received from client: %s\n", buffer);
    close(new_socket);
    close(server_fd);

    return 0;
}
```

  - **Client Code**:

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <arpa/inet.h>

int main() {
    int sock = 0;
    struct sockaddr_in serv_addr;
    char *hello = "Hello from client!";
    char buffer[1024] = {0};

    sock = socket(AF_INET, SOCK_STREAM, 0);
    serv_addr.sin_family = AF_INET;
    serv_addr.sin_port = htons(8080);

    // Convert IPv4 and IPv6 addresses from text to binary form
    inet_pton(AF_INET, "127.0.0.1", &serv_addr.sin_addr);
    connect(sock, (struct sockaddr *)&serv_addr, sizeof(serv_addr));
    send(sock, hello, strlen(hello), 0);
    printf("Message sent from client.\n");
    read(sock, buffer, 1024);
    printf("Server: %s\n", buffer);
    close(sock);

    return 0;
}
```

### Advantages and Disadvantages of Message Passing

| Advantages                                       | Disadvantages                                    |
|--------------------------------------------------|-------------------------------------------------|
| Decouples sender and receiver, promoting modularity| Overhead due to message copying                  |
| Allows for flexible communication patterns        | Can introduce latency, especially in synchronous mode|
| Suitable for distributed systems                  | Requires more complex error handling and reliability mechanisms |
| Can be made reliable with acknowledgment systems  | Message size may be limited by implementation    |

### Summary

Message passing is a powerful IPC mechanism that facilitates communication and synchronization between processes in Linux. 
By using message queues or sockets, developers can implement efficient and robust systems that handle concurrent operations effectively.
Understanding the principles and applications of message passing is crucial for building scalable applications, especially in distributed environments.

Read below section for more for info
---

# Message passing # Part 2

- Message passing can be implemented using various modules and frameworks, each designed for different use cases and environments.
- Here are some common types of message passing modules:

## 1. **Message Queues**
Message queues are one of the most common IPC mechanisms that allow processes to communicate by sending and receiving messages in a queue format.

- **Examples**:
  - **System V Message Queues**: Traditional message queues in Unix/Linux systems, using functions like `msgget()`, `msgsnd()`, and `msgrcv()`.
  - **POSIX Message Queues**: A standardized API available in POSIX-compliant systems, allowing messages to be sent and received using functions like `mq_open()`, `mq_send()`, and `mq_receive()`.

## 2. **Sockets**
Sockets provide a way for processes to communicate over a network or locally, allowing for both stream-oriented and datagram-oriented communication.

- **Types**:
  - **TCP Sockets**: Reliable, connection-oriented communication.
  - **UDP Sockets**: Connectionless, faster communication with no guarantee of message delivery.
  
- **Example**: The example provided earlier demonstrates how to use sockets for client-server communication.

## 3. **Remote Procedure Call (RPC)**
RPC enables a program to execute a procedure on a remote server as if it were a local procedure call, abstracting the underlying message passing.

- **Frameworks**:
  - **gRPC**: A high-performance RPC framework that uses HTTP/2 for transport and Protocol Buffers for serialization.
  - **XML-RPC**: Uses XML to encode the calls and HTTP as a transport mechanism.
  - **JSON-RPC**: Similar to XML-RPC but uses JSON for encoding.

## 4. **Publish/Subscribe Systems**
In a publish/subscribe model, senders (publishers) broadcast messages to multiple receivers (subscribers) without knowing who they are.

- **Examples**:
  - **Apache Kafka**: A distributed streaming platform that provides a robust publish/subscribe system for handling large volumes of data.
  - **RabbitMQ**: A message broker that supports various messaging protocols, allowing for flexible publish/subscribe architectures.
  
## 5. **Message Brokers**
Message brokers act as intermediaries for sending messages between producers and consumers, ensuring reliable message delivery and processing.

- **Examples**:
  - **ActiveMQ**: An open-source message broker that supports various messaging protocols.
  - **Amazon SQS**: A fully managed message queuing service that allows decoupling and scaling of microservices, distributed systems, and serverless applications.
  
## 6. **Inter-Process Communication (IPC) Mechanisms**
Various IPC mechanisms also support message passing:

- **Named Pipes**: Allow processes to communicate with each other using a named pipe that can be accessed by different processes.
  
- **Anonymous Pipes**: Similar to named pipes but do not have a name and are typically used for communication between related processes.

## 7. **Shared Memory with Synchronization**
While shared memory primarily involves processes accessing a common memory segment, it can also include synchronization mechanisms (like semaphores or mutexes) to facilitate message passing.

- **Example**: Processes can write messages to shared memory, while other processes read from it, using semaphores to coordinate access.

### Summary
The choice of message passing module depends on the specific requirements of the application, such as performance, reliability, scalability, and ease of use. 
Understanding the different types of message passing modules helps developers select the most appropriate communication mechanism for their systems.

