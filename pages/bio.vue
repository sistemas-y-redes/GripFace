<template>
  <div class="bio-container">
    <nav class="navbar">
      <div class="artist-name">Gripface</div>
      <div class="social-links">
        <a href="https://instagram.com" target="_blank" rel="noopener noreferrer">
          <svg class="social-icon" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512">
            <path
              d="M224.1 141c-63.6 0-114.9 51.3-114.9 114.9s51.3 114.9 114.9 114.9S339 319.5 339 255.9 287.7 141 224.1 141zm0 189.6c-41.1 0-74.7-33.5-74.7-74.7s33.5-74.7 74.7-74.7 74.7 33.5 74.7 74.7-33.6 74.7-74.7 74.7zm146.4-194.3c0 14.9-12 26.8-26.8 26.8-14.9 0-26.8-12-26.8-26.8s12-26.8 26.8-26.8 26.8 12 26.8 26.8zm76.1 27.2c-1.7-35.9-9.9-67.7-36.2-93.9-26.2-26.2-58-34.4-93.9-36.2-37-2.1-147.9-2.1-184.9 0-35.8 1.7-67.6 9.9-93.9 36.1s-34.4 58-36.2 93.9c-2.1 37-2.1 147.9 0 184.9 1.7 35.9 9.9 67.7 36.2 93.9s58 34.4 93.9 36.2c37 2.1 147.9 2.1 184.9 0 35.9-1.7 67.7-9.9 93.9-36.2 26.2-26.2 34.4-58 36.2-93.9 2.1-37 2.1-147.8 0-184.8zM398.8 388c-7.8 19.6-22.9 34.7-42.6 42.6-29.5 11.7-99.5 9-132.1 9s-102.7 2.6-132.1-9c-19.6-7.8-34.7-22.9-42.6-42.6-11.7-29.5-9-99.5-9-132.1s-2.6-102.7 9-132.1c7.8-19.6 22.9-34.7 42.6-42.6 29.5-11.7 99.5-9 132.1-9s102.7-2.6 132.1 9c19.6 7.8 34.7 22.9 42.6 42.6 11.7 29.5 9 99.5 9 132.1s2.7 102.7-9 132.1z" />
          </svg>
        </a>
      </div>
    </nav>

    <div class="content">
      <div class="bio-text-container">
        <div class="bio-title">
          <h1>Bio</h1>
        </div>
        <div class="spacer"></div>
        <div class="bio-content">
          <p>Aquí va la biografía del artista...</p>
          <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras velit erat,
            consectetur vitae nisi vitae, aliquam lacinia odio. Pellentesque dapibus eget erat eget maximus. Integer a
            libero ac mauris maximus dictum. Aenean vehicula sem non consequat sagittis. Curabitur tristique viverra
            erat
            non finibus. Sed non nulla vel urna sollicitudin egestas vel vel nibh. Donec scelerisque augue eleifend
            ipsum
            rutrum, ac mollis quam aliquam. Morbi quis tempor ligula. Proin felis velit, sagittis non sem eleifend,
            interdum consequat urna. Sed at accumsan nunc. Vestibulum convallis pellentesque nisi nec fermentum. Fusce
            facilisis ligula eros, non vulputate massa posuere id. Nulla luctus, urna eget pellentesque mollis, risus
            tortor hendrerit lorem, vel posuere augue purus non purus. Curabitur nec euismod dolor, ut ornare sem.</p>

          <p> Morbi volutpat commodo dictum. Donec posuere feugiat urna at convallis. Orci varius natoque penatibus et
            magnis dis parturient montes, nascetur ridiculus mus. Pellentesque bibendum accumsan turpis eu scelerisque.
            Pellentesque neque nisl, vulputate quis sem id, placerat laoreet lorem. Vestibulum non augue tellus. Sed
            auctor dui a tellus dictum sollicitudin. Aliquam ac ultrices purus. Vivamus sollicitudin erat vel justo
            rhoncus semper. Etiam accumsan mauris eget malesuada consequat. Donec feugiat in purus eu suscipit. Integer
            nisi elit, facilisis vitae tempor vitae, molestie quis nunc. Aenean at sapien quam. Duis efficitur elit
            lacus.
            Praesent ultricies rutrum nisi, tempor dignissim orci bibendum non.</p>

          <p>Fusce tristique, purus eget convallis tristique, lorem purus molestie leo, at venenatis magna odio sit amet
            sapien. Integer pretium purus sed fermentum porttitor. Vestibulum aliquet convallis volutpat. Integer
            suscipit
            urna ut turpis ornare, in placerat ex pulvinar. Nam rhoncus libero a metus bibendum hendrerit. Fusce
            sagittis
            blandit malesuada. Cras id efficitur quam. Duis ut condimentum purus. Aenean rutrum a neque laoreet tempor.
            Ut
            malesuada convallis elit, at bibendum metus suscipit id. </p>
        </div>
      </div>
    </div>
    <div class="bio-images">
      <!-- Imágenes placeholder, reemplaza las URLs según sea necesario -->
      <img src="/img/gripfaceesculturaweb.webp" alt="Placeholder Image">
    </div>

    <footer class="footer">
      <p>&copy; 2024 Gripface. Todos los derechos reservados.</p>
    </footer>
  </div>
</template>


<style scoped>
html,
body {
  margin: 0 !important;
  padding: 0 !important;
}


.bio-container {
  margin: -8px;
}

.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0px;
  height: 10vh;
}

.artist-name {
  font-size: 32px;
  font-weight: bold;
  margin-left: 2em;
}

.social-links a {
  text-decoration: none;
  color: #333;
  margin-right: 3em;
}

.social-icon {
  margin-right: 3em;
}

.content {
  display: flex;
  justify-content: space-around;
  margin: 0px;
}

.bio-text-container {
  background-color: black;
  color: white;
  padding: 2rem;
  margin: 0px;
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  /* Divide el contenedor en 12 columnas */
  grid-gap: 10px;
  /* Espacio entre los elementos */
  align-items: left;
  /* Centra verticalmente los elementos */
}

.bio-title {
  grid-column: span 3;
}

.spacer {
  grid-column: span 4;
}

.bio-content {
  grid-column: span 5;
}

.bio-images {
  padding: 3em;
  background-color: black;
}

.bio-images img {
  width: 100%;
  margin-bottom: 10px;
}

.footer {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
  background-color: #f0f0f0;
  color: black;
  height: 10em;
}
</style>