# File Upload Management System

A simple full-stack **file upload management system** with a **React frontend** and **Node.js + Express backend**.

## Features
- Upload files to the server
- List all uploaded files
- Download files
- Delete files
- REST API with Express
- File storage with Multer
- JSON-based metadata for file info

## Tech Stack
- **Frontend:** React, Axios, CSS
- **Backend:** Node.js, Express, Multer, UUID
- **Storage:** Local file system (uploads folder + JSON metadata)

## Setup

### Backend
1. Install dependencies:
   ```bash
   cd backend
   npm install
   Run the server:

Example Upload Component
import React, { useState } from "react";
import axios from "axios";

function FileUpload() {
  const [file, setFile] = useState(null);

  const handleSubmit = async (e) => {
    e.preventDefault();
    if (!file) return alert("Select a file first");

    const formData = new FormData();
    formData.append("file", file);

    const res = await axios.post("http://localhost:4000/api/upload", formData, {
      headers: { "Content-Type": "multipart/form-data" },
    });

    if (res.status === 200) alert("File uploaded successfully!");
    else alert("Upload failed");
  };

  return (
    <form onSubmit={handleSubmit}>
      <input type="file" onChange={(e) => setFile(e.target.files[0])} />
      <button type="submit">Upload</button>
    </form>
  );
}

export default FileUpload;
