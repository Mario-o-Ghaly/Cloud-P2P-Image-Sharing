# Cloud P2P Application for Image Sharing

## Table of Contents
- [Description](#Description)
- [Features](#Features)
- [Design Choices](#Design-Choices)

## Description
This project aims to implement a cloud-based peer-to-peer(P2P) environment for image encryption and sharing, emphasizing transparency, load balancing, fault tolerance, and P2P communication. The cloud simply consists of 3 interconnected servers communicating with each other P2P to support leader election, load balancing, and fault tolerance in handling client requests. Moreover, the cloud is associated with a user-oriented discovery service to keep track of active users and the images they offer for sharing. On the other hand, the client side's high-level objective is simply to control image exchange with other clients through ownership and viewer rights.

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
- **Encryption**: Steganography for image and access rights encoding.
