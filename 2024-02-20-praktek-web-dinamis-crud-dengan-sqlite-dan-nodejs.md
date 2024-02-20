## index.ejs

 <!-- views/index.ejs -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title><%= title %></title>
  <style>
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      margin: 20px;
      background-color: #f4f4f4;
    }

    h1 {
      color: #333;
      text-align: center;
    }

    a {
      text-decoration: none;
      padding: 8px 16px;
      background-color: #4CAF50;
      color: white;
      border-radius: 4px;
      transition: background-color 0.3s;
    }

    a:hover {
      background-color: #45a049;
    }

    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 20px;
      box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
      overflow: hidden;
      background-color: white;
      border-radius: 5px;
    }

    th, td {
      border: 1px solid #ddd;
      padding: 12px 15px;
      text-align: left;
    }

    th {
      background-color: #4CAF50;
      color: white;
      font-weight: bold;
    }

    tr:nth-child(even) {
      background-color: #f9f9f9;
    }

    tr:hover {
      background-color: #f5f5f5;
    }

    td a {
      display: inline-block;
      margin-right: 5px;
      padding: 6px 10px;
      background-color: #4285F4;
      color: white;
      border-radius: 3px;
      text-decoration: none;
      transition: background-color 0.3s;
    }

    td a:hover {
      background-color: #357ae8;
    }

    .add-form {
      margin-top: 20px;
      background-color: #fff;
      padding: 20px;
      border-radius: 5px;
      box-shadow: 0 0 20px rgba(0, 0, 0, 0.1);
    }

    .form-label {
      display: block;
      margin-bottom: 8px;
      font-weight: bold;
    }

    .form-input {
      width: 100%;
      padding: 8px;
      margin-bottom: 15px;
      box-sizing: border-box;
    }

    .form-button {
      background-color: #4CAF50;
      color: white;
      padding: 10px 16px;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      transition: background-color 0.3s;
    }

    .form-button:hover {
      background-color: #45a049;
    }
  </style>
</head>
<body>
  <h1><%= title %></h1>
  <a href="/add">Tambah Data</a>
  <table>
    <thead>
      <tr>
        <th>Nama</th>
        <th>Umur</th>
        <th>Alamat</th>
        <th>Aksi</th>
      </tr>
    </thead>
    <tbody>
      <% data.forEach(siswa => { %>
        <tr>
          <td><%= siswa.nama %></td>
          <td><%= siswa.umur %></td>
          <td><%= siswa.alamat %></td>
          <td>
            <a href="/edit/<%= siswa.id %>">Edit</a>
            <a href="/delete/<%= siswa.id %>">Delete</a>
          </td>
        </tr>
      <% }); %>
    </tbody>
  </table>

  <div class="add-form">
    <h2>Tambah Data Siswa</h2>
    <form action="/add" method="post">
      <label for="nama" class="form-label">Nama:</label>
      <input type="text" id="nama" name="nama" class="form-input" required>

      <label for="umur" class="form-label">Umur:</label>
      <input type="number" id="umur" name="umur" class="form-input" required>

      <label for="alamat" class="form-label">Alamat:</label>
      <textarea id="alamat" name="alamat" class="form-input" required></textarea>

      <button type="submit" class="form-button">Tambah Data</button>
    </form>
  </div>
</body>
</html>


## app.js

 const express = require('express');
const bodyParser = require('body-parser');
const path = require('path');
const sqlite3 = require('sqlite3').verbose();

const app = express();
const port = 3000;
const dbPath = path.resolve(__dirname, 'database.db');

// Set up EJS as the view engine
app.set('view engine', 'ejs');
app.set('views', path.join(__dirname, 'views'));

// Middleware for reading the request body
app.use(bodyParser.urlencoded({ extended: true }));
app.use(bodyParser.json());

// Database setup
const db = new sqlite3.Database(dbPath);

db.serialize(() => {
  db.run(`
    CREATE TABLE IF NOT EXISTS biodata (
      id INTEGER PRIMARY KEY AUTOINCREMENT,
      nama TEXT,
      umur INTEGER,
      alamat TEXT
    )
  `);
});

// Route to render the index.ejs file
app.get('/', (req, res) => {
  // Fetch data from the database
  db.all('SELECT * FROM biodata', (err, rows) => {
    if (err) {
      console.error(err.message);
      res.status(500).send('Internal Server Error');
      return;
    }
    res.render('index', { title: 'Biodata CRUD', data: rows });
  });
});

// Route to render the add.ejs file
app.get('/add', (req, res) => {
  res.render('add', { title: 'Tambah Biodata' });
});

// Route to handle form submission for adding a new entry
app.post('/add', (req, res) => {
  const { nama, umur, alamat } = req.body;
  db.run('INSERT INTO biodata (nama, umur, alamat) VALUES (?, ?, ?)', [nama, umur, alamat], (err) => {
    if (err) {
      console.error(err.message);
      res.status(500).send('Internal Server Error');
      return;
    }
    res.redirect('/');
  });
});

// Additional routes for editing and deleting entries

// Start the server
app.listen(port, () => {
  console.log(`Server is running at http://localhost:${port}`);
});



## package.json

 {
  "name": "web-dinamis",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "author": "\\",
  "license": "ISC",
  "dependencies": {
    "body-parser": "^1.20.2",
    "ejs": "^3.1.9",
    "express": "^4.18.2",
    "sqlite3": "^5.1.7"
  },
  "devDependencies": {},
  "description": ""
}



![ahrulgans](https://github.com/smk4hebat/ahrull/assets/156273663/77e4cd42-8069-4255-b2d4-fdd11f53ffb1)

