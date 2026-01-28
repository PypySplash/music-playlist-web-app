# My Playlist - Web Music Management App

A full-stack web application for creating and managing music playlists. 

Built with React, TypeScript, Node.js, Express, and MongoDB.

---

## Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Configuration](#configuration)
  - [Running the App](#running-the-app)
- [Project Structure](#project-structure)
- [API Documentation](#api-documentation)
- [Usage Guide](#usage-guide)
- [License](#license)

---

## Features

✨ **Playlist Management**
- Create, read, update, and delete playlists
- Edit playlist titles and descriptions in real-time
- Responsive grid layout that adapts to screen size

🎵 **Song Management**
- Add songs to playlists with title, artist, and link information
- Edit song details and move songs between playlists
- Delete individual or multiple songs at once
- Clickable song links that open in new tabs

🎯 **User Experience**
- Input validation with user-friendly error messages
- Duplicate name detection for playlists and songs
- Checkbox selection with "select all" functionality
- Delete mode with visual confirmation
- Fully responsive design (RWD)

---

## Tech Stack

### Frontend
- **React 18** - UI library
- **TypeScript** - Type safety
- **Vite** - Build tool and dev server
- **Axios** - HTTP client

### Backend
- **Node.js** - Runtime environment
- **Express** - Web framework
- **MongoDB** - Database
- **Mongoose** - ODM (Object Data Modeling)

---

## Getting Started

### Prerequisites
Before you begin, ensure you have:
- **Node.js v18.17.1** (or compatible version)
- **npm** or **yarn** package manager
- **MongoDB** account (MongoDB Atlas for cloud or local MongoDB)
- **Git** for version control

### Installation

1. **Clone the repository**
```bash
git clone <repository-url>
cd my_playlist
```

2. **Install frontend dependencies**
```bash
cd frontend
yarn install
cd ..
```

3. **Install backend dependencies**
```bash
cd backend
yarn install
cd ..
```

### Configuration

#### Backend Setup

1. Create `.env` file in `/backend`
```bash
cd backend
cp .env.example .env
```

2. Fill in your environment variables:
```bash
PORT=8000
MONGO_URL="mongodb+srv://<username>:<password>@<cluster>.mongodb.net/?retryWrites=true&w=majority"
```

#### Frontend Setup

1. Create `.env` file in `/frontend`
```bash
cd frontend
cp .env.example .env
```

2. Fill in your API URL:
```bash
VITE_API_URL="http://localhost:8000/api"
```

#### Clear MongoDB (Important!)

Before first run, clear your MongoDB to avoid schema conflicts:
- Log in to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
- Navigate to your cluster's Collections
- Delete existing collections or the entire database
- Let the app recreate the schema on first run



### Running the App

1. **Start the backend server**
```bash
cd backend
yarn dev
```
   
You should see:
```bash
Connected to MongoDB
Server running on port http://localhost:8000
```

2. **In a new terminal, start the frontend server**
```bash
cd frontend
yarn dev
```

3. **Open your browser**
   Navigate to `http://localhost:5173` and start using the app!

**Troubleshooting:**
- If you encounter connection errors, verify `.env` files (check for extra semicolons, typos, etc.)
- If MongoDB connection fails, try switching Node.js to v18.17.1:
  ```bash
  fnm use v18.17.1  # if using fnm
  nvm use v18.17.1  # if using nvm
  ```

---

## Project Structure

```
my_playlist/
├── frontend/                # React frontend
│   ├── src/
│   │   ├── components/      # React components (dialogs, playlist view, etc.)
│   │   ├── hooks/           # Custom React hooks (useSongs for data management)
│   │   ├── utils/
│   │   │   ├── client.ts    # API client functions
│   │   │   └── env.ts       # Environment configuration
│   │   ├── App.tsx          # Main app component
│   │   └── main.tsx
│   ├── .env.example
│   ├── vite.config.ts
│   └── package.json
│
├── backend/                 # Express backend
│   ├── src/
│   │   ├── routes/          # API route handlers
│   │   ├── models/          # MongoDB Mongoose schemas
│   │   ├── middleware/      # Express middleware
│   │   └── server.ts        # Main server file
│   ├── .env.example
│   └── package.json
│
└── README.md
```

---

## API Documentation

All API calls are handled through `frontend/src/utils/client.ts`. The client uses Axios with base URL from `VITE_API_URL`.

### Playlist Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/playlists` | Get all playlists |
| POST | `/api/playlists` | Create new playlist |
| PUT | `/api/playlists/:id` | Update playlist details |
| DELETE | `/api/playlists/:id` | Delete playlist |

### Song Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/songs` | Get all songs |
| POST | `/api/songs` | Create new song |
| PUT | `/api/songs/:id` | Update song details |
| DELETE | `/api/songs/:id` | Delete song |

### API Client Functions

```typescript
// Playlists
getPlaylists()                          // Fetch all playlists
createPlaylist(input)                   // Create new playlist
updatePlaylist(id, input)               // Update playlist
deletePlaylist(id)                      // Delete playlist

// Songs
getSongs()                              // Fetch all songs
createSong(input)                       // Create new song
updateSong(id, input)                   // Update song
deleteSong(id)                          // Delete song
```

---

## Usage Guide

### Home Page

**Header & Layout**
- "WP Music" title at the top
- "My Playlists" subtitle
- Responsive grid of playlists (adapts to screen size)

**Playlist Card**
- Shows playlist image, name, and song count
- Click image to open playlist details

**Action Buttons** (Top right)
- **ADD Button**: Opens dialog to create new playlist
  - Input: Playlist name, description
  - Validation: Name is required and must be unique
  
- **DELETE Button**: Activates delete mode
  - Red delete button appears on each playlist card
  - Click red button to delete that playlist
  - Click DONE to exit delete mode

### Playlist Page

**Header Section**
- Displays playlist image, title, and description
- Title and description are editable
- Click text to edit, changes save automatically when you leave the field

**Song Table**
- Checkbox column (with "select all" in header)
- Song title, artist, and link columns
- Click links to open song in new tab
- Edit button on each row to modify song details

**Song Operations**

**ADD Button** (Right side)
- Opens dialog to add new song
- Input: Song title, artist, song link
- Validation: Title is required, must be unique within playlist

**EDIT Button** (On each song)
- Edit: Song title, artist, link
- Add to other playlists: Select playlist and confirm
- Song stays in original playlist (copy, not move)

**DELETE Button** (Right side)
- Select songs using checkboxes
- Click DELETE, confirm in dialog
- All selected songs are deleted
- Shows error if no songs selected

**Key Features**
- Real-time edits for title/description
- Responsive design adjusts to screen size
- Input validation with error messages
- Duplicate name detection

---

## Key Requirements Met

✅ **PERFECT Requirements**
1. **User Prompts**: Appropriate error messages for empty inputs and invalid operations
2. **Duplicate Name Detection**: Playlist names must be unique; song names must be unique within each playlist

✅ **Core Features**
- Full CRUD operations for playlists and songs
- Responsive design (RWD) for all devices
- Real-time editing of playlist metadata
- Song management with cross-playlist functionality
- Checkbox selection with select-all feature
- Visual delete mode with confirmation

---

## Development Notes

### Component Architecture

- **App.tsx**: Main component managing home page and navigation
- **useSongs.tsx**: Custom hook for global state management (playlists & songs)
- **PlaylistDialog.tsx**: Create/edit playlist modal
- **SongDialog.tsx**: Create/edit song modal
- **client.ts**: Centralized API communication

### Database Schema

- **Playlists**: name, description, image, songs (array of song IDs)
- **Songs**: title, artist, link, playlists (array of playlist IDs)

---

## License

This project is created as a coursework assignment for Web Programming.
