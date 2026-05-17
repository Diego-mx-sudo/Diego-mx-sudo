mkdir servidor-tareas
cd servidor-tareas
npm init -y
npm install express cors
server.js
const express = require('express');
const cors = require('cors');

const app = express();

app.use(cors());
app.use(express.json());

let tareas = [
  { id: 1, titulo: 'Estudiar React Native' },
  { id: 2, titulo: 'Hacer actividad de móviles' }
];

// GET -> obtener tareas
app.get('/tareas', (req, res) => {
  res.json(tareas);
});

// POST -> agregar tarea
app.post('/tareas', (req, res) => {
  const nuevaTarea = {
    id: tareas.length + 1,
    titulo: req.body.titulo
  };

  tareas.push(nuevaTarea);

  res.json({
    mensaje: 'Tarea agregada',
    tarea: nuevaTarea
  });
});

const PORT = 3000;

app.listen(PORT, () => {
  console.log(`Servidor ejecutándose en puerto ${PORT}`);
});
