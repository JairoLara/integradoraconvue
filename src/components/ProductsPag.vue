<template>
  <div>
    <!-- Mostrar productos limitados -->
    <div class="container-fluid" id="productos">
      <h1>Lo más vendido</h1>
      <div class="imagen-caja">
        <div class="product-container">
          <div v-for="product in limitedProducts" :key="product.id" class="product">
            <img :src="product.imageUrl" :alt="product.name" @click="viewProductDetails(product)" />
            <div class="product-info">
              <h4>{{ product.name }}</h4>
              <p>{{ `$${product.price}` }}</p>
              <p>{{ product.categoria }}</p>
              <button class="boton-agregar" @click="addToCart(product)">Agregar al carrito</button>
              <button class="boton-favoritos" @click="addToFavorites(product)">Agregar a favoritos</button>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Mostrar todos los productos -->
    <div class="container-fluid text-center" style="background-color: #fab9c3;">
      <h1 style="color: rgb(36, 36, 36);" id="productostod">TODOS LOS PRODUCTOS</h1>
    </div>

    <div id="todosproducts" class="container-fluid text-center">
      <div v-for="product in displayedProducts" :key="product.id" class="product">
        <img :src="product.imageUrl" :alt="product.name" @click="viewProductDetails(product)" />
        <div class="product-info">
          <h4>{{ product.name }}</h4>
          <p>{{ `$${product.price}` }}</p>
          <p>{{ product.categoria }}</p>
          <button class="boton-agregar" @click="addToCart(product)">Agregar al carrito</button>
          <button class="boton-favoritos" @click="addToFavorites(product)">Agregar a favoritos</button>
        </div>
      </div>
    </div>

    <!-- Contenedor para resultados de búsqueda -->
    <div id="results"></div>
  </div>
</template>

<script>
export default {
  name: 'ProductsPag',
  data() {
    return {
      allProducts: [],
      displayedProducts: [],
      limitedProducts: []
    };
  },
  mounted() {
    this.fetchProducts();
  },
  methods: {
    async fetchProducts() {
      try {
        const response = await fetch('https://66a189667053166bcabf3141.mockapi.io/producs');
        if (!response.ok) {
          throw new Error(`HTTP error! Status: ${response.status}`);
        }
        const products = await response.json();
        console.log('Fetched products:', products); // Verifica los datos aquí
        this.allProducts = products;
        this.displayedProducts = products;
        this.limitedProducts = products.slice(0, 4); // Mostrar los primeros 4 productos
      } catch (error) {
        console.error('Error fetching products:', error);
      }
    },
    addToCart(product) {
      let cart = JSON.parse(localStorage.getItem('cart')) || [];
      if (cart.some(item => item.id === product.id)) {
        alert(`${product.name} ya está en el carrito`);
        return;
      }
      cart.push(product);
      localStorage.setItem('cart', JSON.stringify(cart));
      alert(`${product.name} ha sido añadido al carrito`);
    },
    addToFavorites(product) {
      let favorites = JSON.parse(localStorage.getItem('favorites')) || [];
      favorites.push(product);
      localStorage.setItem('favorites', JSON.stringify(favorites));
      alert(`${product.name} ha sido añadido a favoritos`);
    },
    viewProductDetails(product) {
      localStorage.setItem('selectedProduct', JSON.stringify(product));
      window.location.href = 'producto.html';
    },
    searchAPI(query) {
      fetch('https://66a189667053166bcabf3141.mockapi.io/producs')
        .then(response => response.json())
        .then(data => {
          const filteredData = data.filter(item => item.name.toLowerCase().includes(query.toLowerCase()));
          this.displayResults(filteredData);
        })
        .catch(error => console.error('Error:', error));
    },
    displayResults(results) {
      const resultsContainer = document.getElementById('results');
      resultsContainer.innerHTML = '';

      if (results.length === 0) {
        resultsContainer.innerHTML = '<p>No results found</p>';
        return;
      }

      results.forEach(item => {
        const div = document.createElement('div');
        div.classList.add('result-item');
        div.innerHTML = `
          <h3>${item.name}</h3>
          <p>ID: ${item.id}</p>
        `;
        resultsContainer.appendChild(div);
      });
    }
  }
}
</script>

<style scoped>
/* Agrega estilos aquí si es necesario */
</style>