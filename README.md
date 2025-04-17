# Minitalk 📡

A simple client-server communication program using UNIX signals (SIGUSR1 and SIGUSR2).

---

## Table of Contents
- [Introduction](#introduction)
- [Technologies](#technologies)
- [How It Works](#how-it-works)
- [Installation](#installation)
- [Usage](#usage)
- [Example](#example)
- [Bonus Features](#bonus-features)
- [Limitations](#limitations)

---

## Introduction
Minitalk is a project that demonstrates **inter-process communication (IPC)** using **UNIX signals**. It consists of:
- A **server** that displays its PID and waits for messages.
- A **client** that sends messages to the server using signals.

This project is part of the **42 School curriculum** and adheres to strict coding standards (no leaks, no crashes, and efficient signal handling).

---

## Technologies
- Written in **C** (C99 standard)
- Uses UNIX signals (**SIGUSR1** and **SIGUSR2**)
- System calls:  
  `kill()`, `getpid()`, `sigaction()`, `pause()`, `usleep()`

---

## How It Works
### Server (`server.c`)
1. Displays its **PID**.
2. Waits for signals from the client.
3. Converts received signals into characters.
4. Prints the message upon completion.

### Client (`client.c`)
1. Takes a **server PID** and a **message** as arguments.
2. Sends each bit of the message as:
   - `SIGUSR1` = `1`
   - `SIGUSR2` = `0`
3. Sends a **null terminator** (`\0`) to signal the end of the message.

### Bonus Features
- **Unicode support** (UTF-8)
- **Acknowledgement system** (server confirms message receipt)
- **Defensive programming** (error handling for invalid PIDs, etc.)

---

## Installation
```sh
git clone https://github.com/yourusername/minitalk.git
cd minitalk
make        # Compiles both server and client
make bonus  # Compiles the bonus version (if applicable)
