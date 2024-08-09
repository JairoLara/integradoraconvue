<template>
    <div class="container-fluid" id="navs">
      <div class="row">
        <div class="col text-start">
          <a href="index.html"><img src="../assets/imagenes/pixelcut-export.png" style="width: 80%; height: auto; max-width: 80%" /></a>
          <div class="container" style="margin-top: 30px; padding: 0">
            <i>
              <h4 id="opc">
                <a href="#">Inicio |</a>
                <a href="#" class="opc2" id="categorias" style="color: aliceblue;">Categorías |</a>
                  <div id="categoriasMenu" class="categoria-menu" style="display: none;">
                    <button class="categoriaopc" categoria="Belleza"><a href="#productostod" style="color: black;">Belleza</a></button>
                    <button class="categoriaopc" categoria="Papeleria"><a href="#productostod" style="color: black;">Papeleria</a></button>
                    <button class="categoriaopc" categoria="Accesorios"><a href="#productostod" style="color: black;">Accesorios</a></button>
                    <button class="categoriaopc" categoria="Juegos"><a href="#productostod" style="color: black;">Juegos</a></button>
                    <button class="categoriaopc" categoria="Todos"><a href="#productostod" style="color: black;">Todos</a></button>
                  </div>
                <a href="#contacto">Contacto</a>
              </h4>
            </i> 
          </div>
        </div>
        <div class="col text-center">
          <a href="index.html"><img src="../assets/imagenes/logo.png" style="max-width: 40%; height: auto" id="logoop" /></a>
        </div>
        <div class="col text-end" style="margin-top: 50px">
          <div class="container">
            <input type="text" id="search-input" placeholder="Buscar">
            <button id="search-button" class="opc2">
              <span class="material-symbols-outlined inverted-icon">search</span>
              </button>
                
              <button class="opc2" id="view-cart">
                <span class="material-symbols-outlined"> shopping_basket </span>
              </button>
              <div class="dropdown">
                <input type="checkbox" id="dropdown-toggle" class="dropdown-toggle">
                <label for="dropdown-toggle" class="opc2">
                    <span class="material-symbols-outlined" style="cursor: pointer;">account_circle</span>
                </label>
                <div class="dropdown-content">
                  <a href="registroylogin/perfil.php">Mi perfil</a>
                  <a href="./carrito.html">Mis compras</a>
                  <a href="./favoritos.html">Favoritos</a>
                  <a href="registroylogin/logout.php">Cerrar sesión</a>
                </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
  name: 'NavBar',
  data() {
    return {
      searchQuery: ''
    };
  },
  methods: {
    search() {
      this.$emit('search', this.searchQuery);
    },
    viewCart() {
      window.location.href = 'carrito.html';
    },
    toggleCategories() {
      const categoriasMenu = document.getElementById('categoriasMenu');
      categoriasMenu.style.display = categoriasMenu.style.display === 'none' ? 'block' : 'none';
    }
  },
  mounted() {
    document.getElementById('categorias').addEventListener('click', this.toggleCategories);

    document.addEventListener('click', (event) => {
      const categoriasMenu = document.getElementById('categoriasMenu');
      const categorias = document.getElementById('categorias');
      if (!categorias.contains(event.target) && !categoriasMenu.contains(event.target)) {
        categoriasMenu.style.display = 'none';
      }
    });
  }
};
  </script>
  
  <style scoped>
   #navs {
  background-color: #fab9c3;
  padding: 10px 20px;
}
.material-symbols-outlined {
  font-size: 50px;
  color: aliceblue;
}
.inverted-icon {
  transform: scaleX(-1);
}
#opc {
  color: aliceblue;
  font-family: inherit;
}
a {
  text-decoration: none;
  color: aliceblue;
}
.opc2 {
  background-color: #fab9c3;
  border: none;
}
#inicio {
  padding: 0;
  position: relative;
  z-index: 0;
}
#contacto {
  background-color: #fab9c3;
  padding: 10px;
  margin: 0;
}
#coyotelog {
  position: absolute;
  bottom: 100%;
  transform: translateY(61%);
  right: 0;
  z-index: 1;
}
#iconscont {
  max-width: 40%;
  height: auto;
}
.categoria-menu {
  position: fixed;
  background-color: white;
  border-radius: 3px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  z-index: 1000;
  border: 3px solid #fab9c3;
}
.categoriaopc {
  display: block;
  padding: 10px 20px;
  border: none;
  background: none;
  width: 100%;
  text-align: left;
}
.categoriaopc:hover {
  background-color: #fecfd6;
  transition-duration: .5s;
}
.dropdown {
  position: relative;
  display: inline-block;
}
.dropdown-toggle {
  display: none;
}
.dropdown-content {
  display: none;
  position: fixed;
  background-color: white;
  border-radius: 3px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  z-index: 1000;
  border: 3px solid #fab9c3;
  right: 40px;
}
.dropdown-content a {
  color: black;
  padding: 12px 16px;
  text-decoration: none;
  display: block;
}
.dropdown-content a:hover {
  background-color: #fecfd6;
  transition-duration: .5s;
}
.dropdown-toggle:checked ~ .dropdown-content {
  display: block;
}
  </style>