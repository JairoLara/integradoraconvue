<template>
    <div class="container-fluid text-center" id="inicio" style="background-color: rgb(202, 108, 245)">
      <p id="opc"><a href="#">INICIO</a></p>
      <div class="container-fluid" id="contacto">
        <div class="row">
          <div class="col text-center">
            <p id="opc"><strong>¿QUE HACEMOS?</strong></p>
            <p id="opc">
              vendemos artículos cutes a precios accesibles de tus personajes favoritos
            </p>
          </div>
          <div class="col">
            <p id="opc">TEL. +52 871 576 4628</p>
            <i>
              <a href="https://www.facebook.com/profile.php?id=61561594462867&mibextid=ZbWKwL" target="_blank" rel="noopener noreferrer"><img src="../assets/imagenes/icons8-facebook-nuevo-50 1.png" id="iconscont" /></a>
              <a href="https://www.instagram.com/elcoyotito_store?igsh=MW5xeGtpZGNjYWw3ZQ==" target="_blank" rel="noopener noreferrer"><img src="../assets/imagenes/icons8-instagram-30 1.png" id="iconscont" /></a>
              <a href="https://www.tiktok.com/@el.coyotito.store?_t=8oYhLyfbea6&_r=1" target="_blank" rel="noopener noreferrer"><img src="../assets/imagenes/icons8-tik-tok-50 1.png" id="iconscont" /></a>
            </i>
          </div>
          <div class="col">
            <img src="../assets/imagenes/coyotelog.png" id="coyotelog" style="width: 20%; height: auto" />
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'FooterPag'
  }
  </script>
  
  <style scoped>
  #opc {
  color: aliceblue;
  font-family: inherit;
}
a {
  text-decoration: none;
  color: aliceblue;
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
  transform: translateY(55%);
  right: 0;
  z-index: 1;
}
#iconscont {
  max-width: 40%;
  height: auto;
}
  </style>