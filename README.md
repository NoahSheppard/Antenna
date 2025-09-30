# Antenna

Antenna is a prototype messaging application consisting of a C++ client and JavaScript backend. It is in an early, skeletal state, intended primarily as a playground for experimenting with socket-based communication and basic authentication workflows.  

This document describes the current state of the project, its components, limitations, and usage.

---

## Overview

- **Client:**  
  - Written in C++  
  - Currently minimal, incomplete, and loosely structured  
  - Provides only a skeletal framework for connecting to the backend  

- **Backend:**  
  - Written in JavaScript
  - Provides basic user authentication  
  - Exposes endpoints via **GET** and **POST** requests  
  - Socket-based for real-time communication  
  - No relation to the client-side implementation yet  

- **Security:**  
  - **No end-to-end encryption**  
  - Authentication implemented at a basic level (username + password exchange)  
  - Intended for experimentation, **not** production use  

---

## Architecture

### Client
- Language: **C++**
- Functionality:  
  - Skeleton for establishing a socket connection to backend  
  - No message queueing or error handling
  - No message capability, channel querying, or really anything to do with the API
- Role: Proof-of-concept placeholder  

### Backend
- Languages: **JavaScript (primary), C++ (extensions where required)**  
- Functionality:  
  - Manages user accounts (basic username/password storage)  
  - Handles authentication requests via HTTP GET/POST  
  - Provides socket-based communication channels for message passing  
  - Lacks message persistence, history, or scaling support  

---

## Current Features

- Client can connect to backend sockets (in principle).  
- Backend accepts connections and provides basic authentication.  
- Minimal message-passing capability over sockets.
- Server has a database for messages, users, and authentication keys

---

## Limitations

- **Security:**  
  - No end-to-end encryption  
  - Credentials not protected against replay or interception  
  - Not suitable for real-world deployment  

- **Client:**  
  - Incomplete, with no full UI or message handling logic  
  - Skeleton code only  

- **Backend:**  
  - No structured error handling or reconnection strategies  
  - Scaling not implemented  

---

## Usage

### Backend
1. Run the backend server (requires Node.js environment with any native C++ bindings compiled).  
2. Server listens on a configured port for:  
   - **HTTP requests** (authentication)  
   - **Socket connections** (messaging)  

### Client
1. Compile the C++ client skeleton.  
2. Connect to the backend’s socket server.  
3. Authenticate using the username/password mechanism.  
4. Send/receive messages (raw, unencrypted).  

---

## Development Goals

The project is in an early experimental phase. Planned areas of focus include:  
- Implementing actual client logic (message parsing, storage, retries)  
- Backend database integration (persistent user accounts and message history)  
- Basic UI for the client (text-based or GUI)  
- Security improvements (hashing, TLS, optional encryption)  
- Client-backend integration  

---

## Disclaimer

This project is a **prototype** and is **not safe for production use**. Its primary purpose is to demonstrate socket-based client-server communication with rudimentary authentication.  
