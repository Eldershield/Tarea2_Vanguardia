<template>
    <div class="libros">
      <div v-for="libro in libros" :key="libro.id" class="libro">
        <img :src="libro.imagen" :alt="libro.nombre" />
        <h2>{{ libro.nombre }}</h2>
        <p>{{ libro.descripcion }}</p>
        <p><strong>Precio:</strong> ${{ libro.precio }}</p>
        <button @click="agregarAlCarrito(libro)">Agregar al carrito</button>
      </div>
    </div>
  </template>
  <script>
  import { libros } from '../libros.js';
  export default {
    data() {
      return { libros };
    },
    methods: {
      agregarAlCarrito(libro) {
        this.$emit('agregar', libro);
      }
    }
  };
  </script>