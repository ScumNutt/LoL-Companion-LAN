# League Companion - Technical Overview

## Purpose

This document explains the architecture, permissions, and technical behavior of League Companion.

It is intended for developers, contributors, and technical reviewers.

---

# Architecture

PHONE
|
| HTTP / WebSocket
|
LOCAL NETWORK
|
|
PC APPLICATION
|
| Local client communication
|
LEAGUE CLIENT


## Components

### Phone Interface

The phone:

- Displays the remote interface
- Sends commands only after user interaction
- Receives status updates

The phone does not connect directly to Riot services.

---

### PC Application

The PC application:

- Hosts the local interface
- Handles communication with the phone
- Communicates with the running League client
- Maintains temporary session state

It runs as a normal user application.

No administrator privileges required.

---

# Communication

## Phone ↔ PC

Connection:

- Local network only
- Temporary pairing session
- User-controlled access

No external server is required.

---

## PC ↔ League Client

Communication happens through the League client's local interface.

The application:

- Reads current client state
- Sends user-requested actions
- Does not modify League files

---

# User Interaction Model

Every action requires user input.

Examples:

- User presses a button
- Application receives the command
- Application sends the requested action

The application does not:

- decide actions
- perform actions automatically
- run actions in the background

---

# Data Handling

The application does not:

- store Riot passwords
- create Riot accounts
- upload user data
- collect analytics

Local temporary files may be created for:

- settings
- cache
- logs

---

# Limitations

League Companion depends on the League client interface.

Future client updates may affect compatibility.

