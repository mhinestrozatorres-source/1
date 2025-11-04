
# Nuestra_Boda_Margarita_y_Harold/
<!doctype html>
<html lang="es">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Nuestra Boda – Margarita y Harold</title>
    <link rel="icon" href="/favicon.ico" />
  </head>
  <body class="bg-white">
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>


import { motion } from "framer-motion";
import { useEffect, useState } from "react";

export default function App() {
  const [timeLeft, setTimeLeft] = useState("");

  useEffect(() => {
    const countDownDate = new Date("Nov 15, 2025 10:00:00").getTime();
    const interval = setInterval(() => {
      const now = new Date().getTime();
      const distance = countDownDate - now;
      if (distance < 0) {
        setTimeLeft("¡Hoy es el gran día! 💍");
        clearInterval(interval);
      } else {
        const d = Math.floor(distance / (1000 * 60 * 60 * 24));
        const h = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
        const m = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
        const s = Math.floor((distance % (1000 * 60)) / 1000);
        setTimeLeft(`${d} días ${h}h ${m}m ${s}s`);
      }
    }, 1000);
    return () => clearInterval(interval);
  }, []);

  return (
    <div className="text-gray-800">
      <section
        className="relative h-screen flex flex-col items-center justify-center text-white text-center bg-cover bg-center"
        style={{
          backgroundImage:
            "linear-gradient(rgba(0,0,0,0.4), rgba(0,0,0,0.4)), url('/BODA.jpg')",
        }}
      >
        <motion.h1
          initial={{ opacity: 0, y: -20 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 1 }}
          className="text-6xl font-serif mb-3"
        >
          Margarita & Harold
        </motion.h1>
        <motion.p
          initial={{ opacity: 0, y: 20 }}
          animate={{ opacity: 1, y: 0 }}
          transition={{ duration: 1.5 }}
          className="text-lg max-w-xl"
        >
          “Más valen dos que uno, porque obtienen más fruto de su esfuerzo.”<br />
          <em>Eclesiastés 4:9</em>
        </motion.p>
      </section>

      <section className="py-16 bg-rose-50 text-center">
        <h2 className="text-3xl text-rose-700 mb-6 font-serif">Faltan</h2>
        <p className="text-2xl text-green-800">{timeLeft}</p>
      </section>

      <section className="py-20 text-center">
        <h2 className="text-3xl text-green-900 mb-4 font-serif">Ceremonia de Boda</h2>
        <p><strong>Día:</strong> 15 noviembre 2025, 10:00 a.m.</p>
        <p><strong>Lugar:</strong> Parroquia Juan Pablo Segundo</p>
        <p><strong>Dirección:</strong> Barrio Campamento, carrera 16 19N-25, Urb.</p>
        <a
          href="https://maps.app.goo.gl/BkKQshBozQyhcEC46"
          target="_blank"
          className="inline-block mt-4 bg-rose-600 text-white px-5 py-2 rounded-full hover:bg-rose-700"
        >
          Ver en mapa
        </a>
      </section>

      <section className="py-20 text-center bg-rose-50">
        <h2 className="text-3xl text-green-900 mb-4 font-serif">Cena</h2>
        <p><strong>Día:</strong> 15 noviembre 2025, 7:00 p.m.</p>
        <p><strong>Lugar:</strong> Casa de los novios</p>
        <p><strong>Dirección:</strong> Barrio Ciudad Jardín, calle 19N #6a-59</p>
        <a
          href="https://maps.app.goo.gl/wykze673rdxxcwoV7"
          target="_blank"
          className="inline-block mt-4 bg-rose-600 text-white px-5 py-2 rounded-full hover:bg-rose-700"
        >
          Ver en mapa
        </a>
      </section>

      <section className="py-20 text-center">
        <h2 className="text-3xl text-green-900 mb-4 font-serif">Confirma tu Asistencia</h2>
        <form
          action="mailto:mhinestrozatorres@gmail.com"
          method="POST"
          encType="text/plain"
          className="max-w-md mx-auto bg-white p-6 rounded-xl shadow-lg"
        >
          <input
            type="text"
            name="Nombre"
            placeholder="Tu nombre"
            required
            className="w-full p-3 mb-4 border rounded"
          />
          <input
            type="email"
            name="Correo"
            placeholder="Tu correo"
            required
            className="w-full p-3 mb-4 border rounded"
          />
          <div className="mb-4">
            <label className="mr-4">
              <input type="radio" name="Asistencia" value="Sí asistiré" required /> Sí asistiré
            </label>
            <label className="ml-4">
              <input type="radio" name="Asistencia" value="No asistiré" /> No asistiré
            </label>
          </div>
          <button
            type="submit"
            className="bg-rose-600 text-white px-5 py-2 rounded-full hover:bg-rose-700"
          >
            Confirmar asistencia
          </button>
        </form>
      </section>

      <footer className="py-10 bg-rose-50 text-center text-gray-600 text-sm">
        Con amor, Margarita y Harold 💕
      </footer>
    </div>
  );
}


import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App.jsx";
import "./index.css";

ReactDOM.createRoot(document.getElementById("root")).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);


@tailwind base;
@tailwind components;
@tailwind utilities;

body {
  font-family: 'Georgia', serif;
}

package.json

{
  "name": "nuestra-boda-margarita-y-harold",
  "version": "1.0.0",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "framer-motion": "^11.0.0",
    "react": "^18.3.1",
    "react-dom": "^18.3.1"
  },
  "devDependencies": {
    "autoprefixer": "^10.4.18",
    "postcss": "^8.4.35",
    "tailwindcss": "^3.4.3",
    "vite": "^5.0.0"
  }
}


tailwind.config.js

export default {
  content: ["./index.html", "./src/**/*.{js,jsx}"],
  theme: { extend: {} },
  plugins: [],
};


vite.config.js

import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

export default defineConfig({
  plugins: [react()],
});
