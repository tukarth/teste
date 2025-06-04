<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>🎵 Music Votes</title>
  <link rel="stylesheet" href="css/styles.css"/>
</head>
<body>
  <header>
    <h1>🎵 Music Votes</h1>
    <p>Vote nas suas músicas favoritas!</p>
  </header>

  <main>
    <section class="music-list">

      <!-- Música 1 -->
      <div class="music-card">
        <img src="assets/music1.jpg" alt="Blinding Lights">
        <h2>Blinding Lights - The Weeknd</h2>
        <audio controls>
          <source src="assets/blinding-lights.mp3" type="audio/mpeg">
        </audio>
        <div class="buttons">
          <button onclick="likeSong('blinding-lights')">❤️ Like</button>
          <p id="blinding-lights-likes">Likes: 0</p>
        </div>
      </div>

      <!-- Música 2 -->
      <div class="music-card">
        <img src="assets/music2.jpg" alt="Levitating">
        <h2>Levitating - Dua Lipa</h2>
        <audio controls>
          <source src="assets/levitating.mp3" type="audio/mpeg">
        </audio>
        <div class="buttons">
          <button onclick="likeSong('levitating')">❤️ Like</button>
          <p id="levitating-likes">Likes: 0</p>
        </div>
      </div>

      <!-- Música 3 -->
      <div class="music-card">
        <img src="assets/music3.jpg" alt="Peaches">
        <h2>Peaches - Justin Bieber</h2>
        <audio controls>
          <source src="assets/peaches.mp3" type="audio/mpeg">
        </audio>
        <div class="buttons">
          <button onclick="likeSong('peaches')">❤️ Like</button>
          <p id="peaches-likes">Likes: 0</p>
        </div>
      </div>

    </section>
  </main>

  <footer>
    <p>Desenvolvido por Arthur 💚 | 2025</p>
  </footer>

  <script src="js/script.js"></script>
</body>
</html>
