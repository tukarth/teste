<!DOCTYPE html>
<html lang="pt-BR" data-theme="dark">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>🎵 MusicVote - Plataforma de Votos Musicais</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <style>
    :root {
      --primary: #8a2be2;
      --secondary: #4b0082;
      --accent: #ff6b6b;
      --dark: #121212;
      --light: #f8f9fa;
      --gray: #2d2d2d;
      --transition: all 0.3s ease;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    body {
      background: linear-gradient(135deg, var(--dark), #1a1a2e);
      color: var(--light);
      min-height: 100vh;
      padding-bottom: 60px;
    }

    header {
      background: rgba(18, 18, 18, 0.8);
      backdrop-filter: blur(10px);
      padding: 1rem 5%;
      position: sticky;
      top: 0;
      z-index: 100;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
    }

    .logo {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .logo h1 {
      font-size: 1.8rem;
      background: linear-gradient(90deg, var(--accent), var(--primary));
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }

    .nav-links {
      display: flex;
      gap: 2rem;
    }

    .nav-links a {
      color: var(--light);
      text-decoration: none;
      font-weight: 500;
      transition: var(--transition);
      padding: 8px 12px;
      border-radius: 4px;
    }

    .nav-links a:hover {
      background: rgba(255, 255, 255, 0.1);
    }

    .search-bar {
      display: flex;
      background: rgba(255, 255, 255, 0.1);
      border-radius: 30px;
      padding: 8px 15px;
      width: 300px;
    }

    .search-bar input {
      background: transparent;
      border: none;
      color: white;
      width: 100%;
      outline: none;
    }

    .user-actions {
      display: flex;
      gap: 1rem;
    }

    .btn {
      padding: 10px 20px;
      border-radius: 30px;
      border: none;
      font-weight: 600;
      cursor: pointer;
      transition: var(--transition);
    }

    .btn-primary {
      background: var(--primary);
      color: white;
    }

    .btn-outline {
      background: transparent;
      border: 2px solid var(--primary);
      color: var(--primary);
    }

    .btn:hover {
      transform: translateY(-2px);
      box-shadow: 0 4px 15px rgba(138, 43, 226, 0.4);
    }

    .main-container {
      max-width: 1400px;
      margin: 2rem auto;
      padding: 0 2rem;
    }

    .section-title {
      font-size: 1.8rem;
      margin-bottom: 1.5rem;
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .filters {
      display: flex;
      gap: 1rem;
      margin-bottom: 2rem;
      flex-wrap: wrap;
    }

    .filter-btn {
      padding: 8px 20px;
      background: rgba(255, 255, 255, 0.1);
      border: none;
      color: white;
      border-radius: 30px;
      cursor: pointer;
      transition: var(--transition);
    }

    .filter-btn.active, .filter-btn:hover {
      background: var(--primary);
    }

    .music-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
      gap: 2rem;
      margin-bottom: 3rem;
    }

    .music-card {
      background: rgba(30, 30, 46, 0.6);
      border-radius: 12px;
      overflow: hidden;
      transition: var(--transition);
      box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
    }

    .music-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 12px 25px rgba(138, 43, 226, 0.3);
    }

    .card-header {
      position: relative;
    }

    .music-thumb {
      width: 100%;
      height: 180px;
      object-fit: cover;
    }

    .play-btn {
      position: absolute;
      bottom: 15px;
      right: 15px;
      background: var(--primary);
      width: 50px;
      height: 50px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      transition: var(--transition);
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
    }

    .play-btn:hover {
      transform: scale(1.1);
      background: var(--accent);
    }

    .card-body {
      padding: 1.5rem;
    }

    .music-title {
      font-size: 1.4rem;
      margin-bottom: 8px;
    }

    .music-artist {
      color: #aaa;
      margin-bottom: 15px;
      font-size: 1.1rem;
    }

    .music-stats {
      display: flex;
      justify-content: space-between;
      margin-bottom: 15px;
    }

    .stat-item {
      display: flex;
      align-items: center;
      gap: 5px;
      color: #ddd;
    }

    .progress-container {
      background: rgba(255, 255, 255, 0.1);
      height: 5px;
      border-radius: 3px;
      margin-bottom: 15px;
    }

    .progress-bar {
      height: 100%;
      background: var(--accent);
      border-radius: 3px;
      width: 70%;
    }

    .rating-system {
      display: flex;
      justify-content: space-between;
      margin-bottom: 15px;
    }

    .star {
      color: #555;
      cursor: pointer;
      font-size: 1.4rem;
      transition: var(--transition);
    }

    .star.active {
      color: gold;
    }

    .action-buttons {
      display: flex;
      gap: 10px;
    }

    .action-btn {
      flex: 1;
      padding: 10px;
      border-radius: 8px;
      border: none;
      background: rgba(255, 255, 255, 0.1);
      color: white;
      cursor: pointer;
      transition: var(--transition);
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
    }

    .action-btn:hover {
      background: rgba(138, 43, 226, 0.3);
    }

    .action-btn.liked {
      background: rgba(255, 0, 0, 0.2);
      color: #ff6b6b;
    }

    .comments-section {
      background: rgba(30, 30, 46, 0.4);
      border-radius: 8px;
      padding: 1.5rem;
      margin-top: 2rem;
    }

    .comment-form {
      display: flex;
      gap: 10px;
      margin-bottom: 1.5rem;
    }

    .comment-input {
      flex: 1;
      padding: 12px;
      border-radius: 8px;
      border: none;
      background: rgba(255, 255, 255, 0.1);
      color: white;
    }

    .comment-list {
      max-height: 300px;
      overflow-y: auto;
    }

    .comment {
      background: rgba(255, 255, 255, 0.05);
      border-radius: 8px;
      padding: 12px;
      margin-bottom: 12px;
    }

    .comment-header {
      display: flex;
      justify-content: space-between;
      margin-bottom: 8px;
    }

    .comment-user {
      font-weight: bold;
      color: var(--accent);
    }

    .comment-time {
      color: #888;
      font-size: 0.9rem;
    }

    .trending-section {
      background: linear-gradient(135deg, #1a1a2e, #16213e);
      border-radius: 12px;
      padding: 2rem;
      margin-top: 3rem;
    }

    .chart-container {
      height: 300px;
      margin-top: 1.5rem;
    }

    footer {
      text-align: center;
      padding: 2rem;
      background: rgba(18, 18, 18, 0.8);
      margin-top: 3rem;
    }

    @media (max-width: 768px) {
      header {
        flex-direction: column;
        gap: 1rem;
        padding: 1rem;
      }
      
      .search-bar {
        width: 100%;
      }
      
      .music-grid {
        grid-template-columns: 1fr;
      }
    }
  </style>
</head>
<body>
  <header>
    <div class="logo">
      <i class="fas fa-music"></i>
      <h1>MusicVote</h1>
    </div>
    
    <nav class="nav-links">
      <a href="#" class="active"><i class="fas fa-home"></i> Início</a>
      <a href="#"><i class="fas fa-fire"></i> Em Alta</a>
      <a href="#"><i class="fas fa-headphones"></i> Gêneros</a>
      <a href="#"><i class="fas fa-calendar"></i> Lançamentos</a>
    </nav>
    
    <div class="search-bar">
      <i class="fas fa-search"></i>
      <input type="text" placeholder="Buscar músicas, artistas...">
    </div>
    
    <div class="user-actions">
      <button class="btn btn-outline"><i class="fas fa-user-plus"></i> Registrar</button>
      <button class="btn btn-primary"><i class="fas fa-sign-in-alt"></i> Login</button>
    </div>
  </header>

  <div class="main-container">
    <h2 class="section-title"><i class="fas fa-star"></i> Músicas em Destaque</h2>
    
    <div class="filters">
      <button class="filter-btn active">Todas</button>
      <button class="filter-btn">Pop</button>
      <button class="filter-btn">Rock</button>
      <button class="filter-btn">Hip Hop</button>
      <button class="filter-btn">Eletrônica</button>
      <button class="filter-btn">Brasileira</button>
    </div>
    
    <div class="music-grid">
      <!-- Música 1 -->
      <div class="music-card">
        <div class="card-header">
          <img src="https://source.unsplash.com/random/600x400/?music,concert" alt="Blinding Lights" class="music-thumb">
          <div class="play-btn">
            <i class="fas fa-play"></i>
          </div>
        </div>
        
        <div class="card-body">
          <h3 class="music-title">Blinding Lights</h3>
          <p class="music-artist">The Weeknd</p>
          
          <div class="music-stats">
            <div class="stat-item">
              <i class="fas fa-play-circle"></i> 245M
            </div>
            <div class="stat-item">
              <i class="fas fa-clock"></i> 3:22
            </div>
            <div class="stat-item">
              <i class="fas fa-calendar"></i> 2020
            </div>
          </div>
          
          <div class="progress-container">
            <div class="progress-bar" style="width: 85%"></div>
          </div>
          
          <div class="rating-system">
            <div class="star" data-value="1"><i class="far fa-star"></i></div>
            <div class="star" data-value="2"><i class="far fa-star"></i></div>
            <div class="star" data-value="3"><i class="far fa-star"></i></div>
            <div class="star" data-value="4"><i class="far fa-star"></i></div>
            <div class="star" data-value="5"><i class="far fa-star"></i></div>
          </div>
          
          <div class="action-buttons">
            <button class="action-btn like-btn" data-id="1">
              <i class="far fa-heart"></i> Curtir
            </button>
            <button class="action-btn">
              <i class="far fa-comment"></i> Comentar
            </button>
            <button class="action-btn">
              <i class="fas fa-share-alt"></i> Compartilhar
            </button>
          </div>
        </div>
        
        <div class="comments-section">
          <div class="comment-form">
            <input type="text" class="comment-input" placeholder="Adicione um comentário...">
            <button class="action-btn">Enviar</button>
          </div>
          
          <div class="comment-list">
            <div class="comment">
              <div class="comment-header">
                <span class="comment-user">Maria Silva</span>
                <span class="comment-time">2 horas atrás</span>
              </div>
              <p>Essa música nunca sai da minha playlist! Melhor do The Weeknd!</p>
            </div>
            
            <div class="comment">
              <div class="comment-header">
                <span class="comment-user">João Santos</span>
                <span class="comment-time">Ontem</span>
              </div>
              <p>Nostálgica demais, me lembra 2020!</p>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Música 2 -->
      <div class="music-card">
        <div class="card-header">
          <img src="https://source.unsplash.com/random/600x400/?music,festival" alt="Levitating" class="music-thumb">
          <div class="play-btn">
            <i class="fas fa-play"></i>
          </div>
        </div>
        
        <div class="card-body">
          <h3 class="music-title">Levitating</h3>
          <p class="music-artist">Dua Lipa</p>
          
          <div class="music-stats">
            <div class="stat-item">
              <i class="fas fa-play-circle"></i> 187M
            </div>
            <div class="stat-item">
              <i class="fas fa-clock"></i> 3:45
            </div>
            <div class="stat-item">
              <i class="fas fa-calendar"></i> 2021
            </div>
          </div>
          
          <div class="progress-container">
            <div class="progress-bar" style="width: 78%"></div>
          </div>
          
          <div class="rating-system">
            <div class="star" data-value="1"><i class="far fa-star"></i></div>
            <div class="star" data-value="2"><i class="far fa-star"></i></div>
            <div class="star" data-value="3"><i class="far fa-star"></i></div>
            <div class="star" data-value="4"><i class="far fa-star"></i></div>
            <div class="star" data-value="5"><i class="far fa-star"></i></div>
          </div>
          
          <div class="action-buttons">
            <button class="action-btn like-btn" data-id="2">
              <i class="far fa-heart"></i> Curtir
            </button>
            <button class="action-btn">
              <i class="far fa-comment"></i> Comentar
            </button>
            <button class="action-btn">
              <i class="fas fa-share-alt"></i> Compartilhar
            </button>
          </div>
        </div>
      </div>
      
      <!-- Música 3 -->
      <div class="music-card">
        <div class="card-header">
          <img src="https://source.unsplash.com/random/600x400/?music,studio" alt="Peaches" class="music-thumb">
          <div class="play-btn">
            <i class="fas fa-play"></i>
          </div>
        </div>
        
        <div class="card-body">
          <h3 class="music-title">Peaches</h3>
          <p class="music-artist">Justin Bieber ft. Daniel Caesar</p>
          
          <div class="music-stats">
            <div class="stat-item">
              <i class="fas fa-play-circle"></i> 156M
            </div>
            <div class="stat-item">
              <i class="fas fa-clock"></i> 3:18
            </div>
            <div class="stat-item">
              <i class="fas fa-calendar"></i> 2021
            </div>
          </div>
          
          <div class="progress-container">
            <div class="progress-bar" style="width: 92%"></div>
          </div>
          
          <div class="rating-system">
            <div class="star" data-value="1"><i class="far fa-star"></i></div>
            <div class="star" data-value="2"><i class="far fa-star"></i></div>
            <div class="star" data-value="3"><i class="far fa-star"></i></div>
            <div class="star" data-value="4"><i class="far fa-star"></i></div>
            <div class="star" data-value="5"><i class="far fa-star"></i></div>
          </div>
          
          <div class="action-buttons">
            <button class="action-btn like-btn" data-id="3">
              <i class="far fa-heart"></i> Curtir
            </button>
            <button class="action-btn">
              <i class="far fa-comment"></i> Comentar
            </button>
            <button class="action-btn">
              <i class="fas fa-share-alt"></i> Compartilhar
            </button>
          </div>
        </div>
      </div>
    </div>
    
    <div class="trending-section">
      <h2 class="section-title"><i class="fas fa-chart-line"></i> Tendências Musicais</h2>
      <div class="chart-container" id="trendingChart">
        <!-- Gráfico seria implementado com Chart.js -->
      </div>
    </div>
  </div>

  <footer>
    <p>Desenvolvido por Arthur 💚 | MusicVote &copy; 2025 - Todos os direitos reservados</p>
  </footer>

  <script>
    document.addEventListener('DOMContentLoaded', function() {
      // Sistema de Likes
      const likeButtons = document.querySelectorAll('.like-btn');
      likeButtons.forEach(button => {
        button.addEventListener('click', function() {
          const musicId = this.getAttribute('data-id');
          this.classList.toggle('liked');
          const icon = this.querySelector('i');
          
          if (this.classList.contains('liked')) {
            this.innerHTML = `<i class="fas fa-heart"></i> Curtido`;
            this.style.background = 'rgba(255, 0, 0, 0.2)';
            this.style.color = '#ff6b6b';
            // Salvar no localStorage
            localStorage.setItem(`music_${musicId}_liked`, 'true');
          } else {
            this.innerHTML = `<i class="far fa-heart"></i> Curtir`;
            this.style.background = '';
            this.style.color = '';
            localStorage.removeItem(`music_${musicId}_liked`);
          }
        });
      });

      // Sistema de Avaliação por Estrelas
      const starRatings = document.querySelectorAll('.rating-system');
      starRatings.forEach(ratingSystem => {
        const stars = ratingSystem.querySelectorAll('.star');
        stars.forEach(star => {
          star.addEventListener('click', function() {
            const value = this.getAttribute('data-value');
            const musicId = this.closest('.music-card').querySelector('.like-btn').getAttribute('data-id');
            
            // Atualizar visual das estrelas
            stars.forEach((s, index) => {
              if (index < value) {
                s.innerHTML = '<i class="fas fa-star"></i>';
                s.classList.add('active');
              } else {
                s.innerHTML = '<i class="far fa-star"></i>';
                s.classList.remove('active');
              }
            });
            
            // Salvar avaliação
            localStorage.setItem(`music_${musicId}_rating`, value);
          });
        });
      });

      // Botões de Play
      const playButtons = document.querySelectorAll('.play-btn');
      playButtons.forEach(button => {
        button.addEventListener('click', function() {
          const icon = this.querySelector('i');
          if (icon.classList.contains('fa-play')) {
            icon.classList.remove('fa-play');
            icon.classList.add('fa-pause');
          } else {
            icon.classList.remove('fa-pause');
            icon.classList.add('fa-play');
          }
        });
      });

      // Carregar estado salvo
      function loadSavedState() {
        likeButtons.forEach(button => {
          const musicId = button.getAttribute('data-id');
          if (localStorage.getItem(`music_${musicId}_liked`) === 'true') {
            button.classList.add('liked');
            button.innerHTML = `<i class="fas fa-heart"></i> Curtido`;
            button.style.background = 'rgba(255, 0, 0, 0.2)';
            button.style.color = '#ff6b6b';
          }
          
          const rating = localStorage.getItem(`music_${musicId}_rating`);
          if (rating) {
            const stars = button.closest('.music-card').querySelectorAll('.star');
            stars.forEach((star, index) => {
              if (index < rating) {
                star.innerHTML = '<i class="fas fa-star"></i>';
                star.classList.add('active');
              }
            });
          }
        });
      }

      loadSavedState();
    });
  </script>
</body>
</html>
