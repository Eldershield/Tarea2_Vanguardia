<template>
    <div class="carrito">
      <h2>Carrito de Compras</h2>
      <div v-for="item in carrito" :key="item.id" class="item">
        <img :src="item.imagen" :alt="item.nombre" />
        <p>{{ item.nombre }}</p>
        <p>${{ item.precio }}</p>
        <button @click="cambiarCantidad(item, -1)">-</button>
        <span>{{ item.cantidad }}</span>
        <button @click="cambiarCantidad(item, 1)">+</button>
      </div>
      <h3>Total: ${{ total }}</h3>
    </div>
  </template>
  <script>
  export default {
    props: ['carrito'],
    computed: {
      total() {
        return this.carrito.reduce((sum, item) => sum + item.precio * item.cantidad, 0).toFixed(2);
      }
    },
    methods: {
      cambiarCantidad(item, cantidad) {
        item.cantidad += cantidad;
        if (item.cantidad < 1) {
          this.$emit('eliminar', item);
        }
      }
    }
  };
  </script>
  