# DriftShare

**DriftShare** is a web-based file sharing application designed to transfer files between two users through a temporary room-based connection.
The project was developed as a final graduation project and focuses on providing a simple, fast, and direct way to share files without requiring user accounts or complex configuration.

---

## Overview

DriftShare allows a sender to create a temporary room number and share it with a receiver.
Once the receiver joins the room, the sender can upload a file and transfer it in real time through a WebSocket connection.

The application combines a static frontend interface with a Node.js backend, using Socket.IO for real-time communication and MongoDB to manage temporary connection identifiers.

---

## Main Features

- Temporary room-based file sharing
- Sender and receiver workflow
- Real-time communication using Socket.IO
- File transfer using binary chunks
- Unique room ID generation
- MongoDB-based room ID management
- Simple and responsive web interface
- Static pages for landing, receiving, contact, FAQ and other sections

---

## How It Works

1. The sender creates a temporary room.
2. The server generates a unique room number.
3. The receiver enters the room number to join the transfer session.
4. The sender selects a file from their device.
5. The file is read in binary format and split into chunks.
6. Chunks are transferred in real time through Socket.IO.
7. The receiver reconstructs the file and downloads it locally.

---

## Tech Stack

### Frontend
- HTML5
- CSS3 / SCSS
- JavaScript
- Bootstrap
- jQuery
- Font Awesome

### Backend
- Node.js
- Express.js
- Socket.IO
- MongoDB
- dotenv

### Development Tools
- Gulp
- BrowserSync
- Sass compiler
- Autoprefixer
- Clean CSS

---

## Project Structure

```text
DriftShare/
│
├── public/
│   ├── assets/
│   │   ├── css/
│   │   ├── images/
│   │   ├── js/
│   │   │   ├── code.js
│   │   │   ├── receiver.js
│   │   │   ├── style.js
│   │   │   └── utils.js
│   │   ├── scss/
│   │   └── vendors/
│   │
│   ├── index.html
│   ├── receiver.html
│   └── contact.html
│
├── server.js
├── gulpfile.js
├── package.json
├── package-lock.json
├── .env.example
└── README.md
```

---

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/espoupou/Driftshare.git
cd Driftshare
```

### 2. Install dependencies

```bash
npm install
```

### 3. Configure environment variables

Create a `.env` file based on `.env.example`:

```bash
cp .env.example .env
```

Then update the MongoDB configuration:

```env
MONGO_HOST=your-mongodb-host
MONGO_USERNAME=your-username
MONGO_PASSWORD=your-password
MONGO_DB_NAME=your-database-name
```

> **Note:** Make sure the variable names in your `.env` file match those used in `server.js`. In particular, verify that `MONGO_DB_NAME` is consistent across both files — a mismatch will cause a MongoDB connection error on startup.

### 4. Run the server

```bash
node server.js
```

The application will be available at:

```
http://localhost:8000
```

---

## Available Scripts

```bash
npm start
```

Runs the Gulp watch task for frontend development.

```bash
npm run vendors
```

Builds vendor assets using Gulp.

---

## Usage

### Sender

1. Open the application in your browser.
2. Click on the button to create a room.
3. Copy the generated room number.
4. Share the room number with the receiver.
5. Select a file to upload and send.

### Receiver

1. Open the receiver page.
2. Enter the room number shared by the sender.
3. Join the room.
4. Wait for the file transfer to start.
5. The file will be downloaded once the transfer is complete.

---

## Key Implementation Details

### Room ID Generation

DriftShare generates a temporary room ID and stores it in MongoDB to avoid duplicate active IDs.

### Real-Time Communication

Socket.IO is used to manage:

- Sender connection
- Receiver connection
- Room initialization
- File metadata transfer
- Binary file chunk transfer
- Transfer progress updates

### File Transfer Logic

The file is read as an `ArrayBuffer`, split into chunks, then sent through WebSocket events.
The receiver collects the chunks, rebuilds the file as a `Blob`, and downloads it locally.

---

## Current Status

This project is an academic prototype developed as a final graduation project.
It demonstrates the core logic of a temporary real-time file sharing system.

---

## Possible Improvements

- Add authentication for private transfers
- Add end-to-end encryption
- Improve transfer speed and reliability for large files
- Add drag-and-drop preview
- Add file size limit management
- Add transfer cancellation
- Add better error handling
- Add deployment configuration
- Add responsive UI improvements
- Add automated tests
- Add Docker support

---

## Security Notes

This project should be reviewed before production use.

Recommended improvements before deployment:

- Validate file size and file type
- Add rate limiting
- Secure Socket.IO events
- Add environment-specific configuration
- Avoid exposing sensitive database credentials
- Add HTTPS support
- Add proper error handling for disconnected users

---

## Author

Developed by **Kokou Espoir ATIVON**.

---

## License

This project is currently not distributed under a specific license.
