<template>
    <div id="app">
      <Header />
      <Libros @agregar="agregarAlCarrito" />
      <Carrito :carrito="carrito" @eliminar="eliminarDelCarrito" />
      <Footer />
    </div>
  </template>
  <script>
  import Header from './Header.vue';
  import Libros from './Libros.vue';
  import Carrito from './Carrito.vue';
  import Footer from './Footer.vue';
  
  export default {
    components: { Header, Libros, Carrito, Footer },
    data() {
      return { carrito: [] };
    },
    methods: {
      agregarAlCarrito(libro) {
        let item = this.carrito.find(l => l.id === libro.id);
        if (item) {
          item.cantidad++;
        } else {
          this.carrito.push({ ...libro, cantidad: 1 });
        }
      },
      eliminarDelCarrito(libro) {
        this.carrito = this.carrito.filter(l => l.id !== libro.id);
      }
    }
  };
  </script>
