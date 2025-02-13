# Cloud P2P Application for Image Sharing

## Table of Contents
- [Description](#Description)
- [Usage](#Usage)
- [Features](#Features)
- [Design Choices](#Design-Choices)
- [Team Members](#Team-Members)

## Description
This project aims to implement a cloud-based peer-to-peer(P2P) environment for image encryption and sharing, emphasizing transparency, load balancing, fault tolerance, and P2P communication. The cloud simply consists of 3 interconnected servers communicating with each other P2P to support leader election, load balancing, and fault tolerance in handling client requests. Moreover, the cloud is associated with a user-oriented discovery service to keep track of active users and the images they offer for sharing. On the other hand, the client side's high-level objective is simply to control image exchange with other clients through ownership and viewer rights.

## Usage
This project consists of 3 interconnected servers to implement leader election for client requests, load balancing, and fault tolerance. This serves as a cloud that the user application communicates with. On the other hand, the project offers the following use cases for the user:
### **Register:** Get a globally unique ID upon registration.

1. **Register** to the cloud and the user gets a globally unique ID.
2. **Sign-in** to the could using his unique ID, and if there are any image access rights updates, they would be enforced as soon as they sign in.
3. **Encrypt Image** by entering the image path, and then the image is sent to the cloud for being encoded on a default image, and then the encoded image is returned.
4. **Request a List of Active Users & Their Images** so that the user can know what else is being offered.
5. **Request Image** from a user by entering from the list the client's number, image ID, and requested number of views.
6. **View Client Requests** which are queued whenever a peer user requests an image from them, and the owner then chooses to see what has been requested, and whether to accept or reject the request.
7. **View Peer Images** which are images requested from other peers and accepted for specific access rights. When the permitted number of views goes to 0, the default image is shown. 
8. **Request Additional Views** for a peer image whose request has been accepted and received already. If the requester goes down, the peer would notify the cloud with the updated access rights and the requester details so that when the requester goes up again, the cloud would enforce them when they sign in.
9. **Enforce Access Rights Updates** by making the owner of an image change the already given number of views for an image to a peer user.
10. **Shut down** properly by notifying the cloud.

## Features
- **Leader Election**: Uses Gholipour’s improved Bully algorithm for leader election, reducing message communication overhead.
- **Load Balancing**: Real-time priority assignment based on CPU load average, ensuring fair distribution of workload among servers.
- **Fault Tolerance**: Detects server failures and reassigns client requests to available servers without affecting user experience.
- **Directory of Service (DoS)**: Centralized MySQL database to track active users, their status, and image-sharing information.
- **Image Encryption**: Uses steganography to embed hidden images within cover images and encode access rights.
- **Client-Server Communication**: Supports user registration, authentication, image encryption, and peer discovery.
- **Peer-to-Peer Communication**: Enables image sharing and access rights modification between clients.
- **Dynamic Port Allocation**: Efficient resource management through dynamic port allocation for client-server and client-client communication.

## Design Choices
- **Leader Election**: Gholipour’s improved Bully algorithm.
- **Load Balancing**: Real-time priority based on CPU load average.
- **Fault Tolerance**: Heartbeat messages and failure detection.
- **DoS**: Centralized MySQL database hosted on Aiven.
- **Serialization**: JSON for metadata and image chunking for image transfer.
- **Coding Framework**: Tokio crate for asynchronous UDP communication.
- **Communication**: UDP in server-to-server, client-to-server, and server-to-client communications
- **Encryption**: Steganography for image and access rights encoding.

## Team Members
- Mario Ghaly - https://github.com/Mario-o-Ghaly
- Ahmed Amr Salah - https://github.com/ahmed-amr-salah
- Amna Elsaqa - https://github.com/Amna-Elsaqa
- Hamza Algobba - https://github.com/Hamza-algobba
