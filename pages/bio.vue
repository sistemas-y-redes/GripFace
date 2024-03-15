<template>
    <div class="bio-container">
      <nav class="navbar">
        <div class="artist-name">Nombre del Artista</div>
        <div class="social-links">
          <!-- Asegúrate de incluir Font Awesome o tu elección de íconos en tu proyecto -->
          <a href="https://instagram.com" target="_blank" rel="noopener noreferrer">
            <i class="fab fa-instagram"></i> Instagram
          </a>
        </div>
      </nav>
  
      <div class="content">
        <div class="bio-text">
          <h1>Bio</h1>
          <p>Aquí va la biografía del artista...</p>
        </div>
        <div class="bio-images">
          <!-- Imágenes placeholder, reemplaza las URLs según sea necesario -->
          <img src="https://via.placeholder.com/300" alt="Placeholder Image">
          <img src="https://via.placeholder.com/300" alt="Placeholder Image">
          <img src="https://via.placeholder.com/300" alt="Placeholder Image">
        </div>
      </div>
  
      <footer class="footer">
        <p>&copy; 2024 Nombre del Artista. Todos los derechos reservados.</p>
      </footer>
    </div>
  </template>
  
  <style scoped>
  .navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 20px;
    background-color: #f0f0f0;
  }
  
  .artist-name {
    font-size: 24px;
    font-weight: bold;
  }
  
  .social-links a {
    text-decoration: none;
    color: #333;
    margin-left: 15px;
  }
  
  .content {
    display: flex;
    justify-content: space-around;
    margin: 20px;
  }
  
  .bio-text {
    flex-basis: 60%;
  }
  
  .bio-images {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    flex-basis: 30%;
  }
  
  .bio-images img {
    width: 100%;
    margin-bottom: 10px;
  }
  
  .footer {
    text-align: center;
    padding: 20px;
    background-color: #f0f0f0;
  }
  </style>
  