<!DOCTYPE html>
<html lang="pt-BR" data-theme="auto">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>🎧 SoundVote - Plataforma Premium</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <style>
    :root {
      --primary: #8a2be2;
      --primary-dark: #6a1cb9;
      --secondary: #4b0082;
      --accent: #ff6b6b;
      --accent-dark: #e05555;
      --dark: #121212;
      --darker: #0a0a0a;
      --light: #f8f9fa;
      --lighter: #ffffff;
      --gray: #2d2d2d;
      --gray-light: #4a4a4a;
      --text-dark: #333;
      --text-light: #f0f0f0;
      --transition: all 0.3s ease;
      --shadow: 0 10px 25px rgba(0,0,0,0.2);
      --shadow-hover: 0 15px 35px rgba(138, 43, 226, 0.25);
      --radius: 16px;
      --radius-sm: 8px;
    }

    .dark-theme {
      --bg-primary: var(--dark);
      --bg-secondary: var(--darker);
      --bg-card: rgba(30, 30, 46, 0.6);
      --bg-comment: rgba(255, 255, 255, 0.05);
      --text-primary: var(--text-light);
      --text-secondary: #aaa;
      --border-color: rgba(255,255,255,0.1);
    }

    .light-theme {
      --bg-primary: #f0f2f5;
      --bg-secondary: var(--lighter);
      --bg-card: rgba(255, 255, 255, 0.8);
      --bg-comment: rgba(0, 0, 0, 0.03);
      --text-primary: var(--text-dark);
      --text-secondary: #666;
      --border-color: rgba(0,0,0,0.1);
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', system-ui, -apple-system, sans-serif;
      transition: background-color 0.3s, color 0.3s;
    }

    body {
      background: var(--bg-primary);
      color: var(--text-primary);
      min-height: 100vh;
      line-height: 1.6;
    }

    /* HEADER STYLES */
    header {
      background: rgba(18, 18, 18, 0.95);
      backdrop-filter: blur(15px);
      padding: 0.8rem 5%;
      position: sticky;
      top: 0;
      z-index: 1000;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: var(--shadow);
      border-bottom: 1px solid var(--border-color);
    }

    .logo {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .logo-icon {
      font-size: 2rem;
      color: var(--accent);
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0% { transform: scale(1); }
      50% { transform: scale(1.1); }
      100% { transform: scale(1); }
    }

    .logo h1 {
      font-size: 2rem;
      font-weight: 800;
      background: linear-gradient(90deg, var(--accent), var(--primary));
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      letter-spacing: -0.5px;
    }

    .nav-links {
      display: flex;
      gap: 2rem;
    }

    .nav-links a {
      color: var(--text-light);
      text-decoration: none;
      font-weight: 600;
      transition: var(--transition);
      padding: 10px 15px;
      border-radius: var(--radius-sm);
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .nav-links a:hover, .nav-links a.active {
      background: rgba(255, 255, 255, 0.1);
    }

    .nav-links a i {
      font-size: 1.1rem;
    }

    .search-bar {
      display: flex;
      align-items: center;
      background: rgba(255, 255, 255, 0.12);
      border-radius: 50px;
      padding: 10px 20px;
      width: 380px;
      transition: var(--transition);
    }

    .search-bar:focus-within {
      background: rgba(255, 255, 255, 0.2);
      box-shadow: 0 0 0 3px rgba(138, 43, 226, 0.3);
    }

    .search-bar input {
      background: transparent;
      border: none;
      color: white;
      width: 100%;
      outline: none;
      font-size: 1rem;
      padding-left: 10px;
    }

    .user-actions {
      display: flex;
      gap: 15px;
    }

    .btn {
      padding: 12px 28px;
      border-radius: 50px;
      border: none;
      font-weight: 700;
      cursor: pointer;
      transition: var(--transition);
      display: flex;
      align-items: center;
      gap: 10px;
      font-size: 1rem;
    }

    .btn-primary {
      background: var(--primary);
      color: white;
      box-shadow: 0 4px 15px rgba(138, 43, 226, 0.4);
    }

    .btn-primary:hover {
      background: var(--primary-dark);
      transform: translateY(-3px);
      box-shadow: 0 7px 20px rgba(138, 43, 226, 0.5);
    }

    .btn-outline {
      background: transparent;
      border: 2px solid var(--primary);
      color: var(--primary);
    }

    .btn-outline:hover {
      background: rgba(138, 43, 226, 0.1);
    }

    .theme-switcher {
      background: rgba(255, 255, 255, 0.1);
      width: 50px;
      height: 50px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      transition: var(--transition);
      border: none;
      color: white;
      font-size: 1.2rem;
    }

    .theme-switcher:hover {
      background: rgba(255, 255, 255, 0.2);
      transform: rotate(20deg);
    }

    /* MAIN CONTENT */
    .main-container {
      max-width: 1600px;
      margin: 2.5rem auto;
      padding: 0 3rem;
    }

    .hero-section {
      text-align: center;
      padding: 4rem 0;
      background: linear-gradient(135deg, rgba(138, 43, 226, 0.15), transparent);
      border-radius: var(--radius);
      margin-bottom: 3rem;
      position: relative;
      overflow: hidden;
    }

    .hero-section::before {
      content: "";
      position: absolute;
      top: -50%;
      left: -50%;
      width: 200%;
      height: 200%;
      background: radial-gradient(circle, rgba(138, 43, 226, 0.08) 0%, transparent 70%);
      z-index: -1;
    }

    .hero-section h2 {
      font-size: 3.5rem;
      font-weight: 900;
      margin-bottom: 1rem;
      background: linear-gradient(90deg, var(--accent), var(--primary));
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
      letter-spacing: -1px;
    }

    .hero-section p {
      font-size: 1.3rem;
      max-width: 700px;
      margin: 0 auto 2rem;
      color: var(--text-secondary);
    }

    .section-title {
      font-size: 2.2rem;
      margin-bottom: 2rem;
      display: flex;
      align-items: center;
      gap: 15px;
    }

    .section-title i {
      background: linear-gradient(135deg, var(--accent), var(--primary));
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }

    .filters {
      display: flex;
      gap: 1rem;
      margin-bottom: 2.5rem;
      flex-wrap: wrap;
    }

    .filter-btn {
      padding: 10px 25px;
      background: rgba(138, 43, 226, 0.1);
      border: 2px solid var(--primary);
      color: var(--primary);
      border-radius: 50px;
      cursor: pointer;
      transition: var(--transition);
      font-weight: 600;
      font-size: 1rem;
    }

    .filter-btn.active, .filter-btn:hover {
      background: var(--primary);
      color: white;
      box-shadow: 0 5px 15px rgba(138, 43, 226, 0.3);
    }

    .music-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
      gap: 2.5rem;
      margin-bottom: 4rem;
    }

    .music-card {
      background: var(--bg-card);
      border-radius: var(--radius);
      overflow: hidden;
      transition: var(--transition);
      box-shadow: var(--shadow);
      border: 1px solid var(--border-color);
      backdrop-filter: blur(10px);
    }

    .music-card:hover {
      transform: translateY(-10px);
      box-shadow: var(--shadow-hover);
    }

    .card-header {
      position: relative;
    }

    .music-thumb {
      width: 100%;
      height: 220px;
      object-fit: cover;
      display: block;
    }

    .music-badge {
      position: absolute;
      top: 15px;
      left: 15px;
      background: var(--accent);
      color: white;
      padding: 5px 15px;
      border-radius: 20px;
      font-size: 0.9rem;
      font-weight: 700;
    }

    .play-btn {
      position: absolute;
      bottom: 20px;
      right: 20px;
      background: var(--primary);
      width: 60px;
      height: 60px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      transition: var(--transition);
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
      border: none;
    }

    .play-btn:hover {
      transform: scale(1.1);
      background: var(--accent);
      box-shadow: 0 7px 20px rgba(255, 107, 107, 0.4);
    }

    .play-btn i {
      color: white;
      font-size: 1.5rem;
    }

    .card-body {
      padding: 1.8rem;
    }

    .music-title {
      font-size: 1.6rem;
      font-weight: 800;
      margin-bottom: 8px;
      letter-spacing: -0.5px;
    }

    .music-artist {
      color: var(--text-secondary);
      margin-bottom: 1.5rem;
      font-size: 1.2rem;
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .music-artist img {
      width: 30px;
      height: 30px;
      border-radius: 50%;
      object-fit: cover;
    }

    .music-stats {
      display: flex;
      justify-content: space-between;
      margin-bottom: 1.5rem;
      flex-wrap: wrap;
      gap: 15px;
    }

    .stat-item {
      display: flex;
      align-items: center;
      gap: 8px;
      font-size: 1rem;
    }

    .stat-item i {
      color: var(--accent);
    }

    .progress-container {
      background: rgba(255, 255, 255, 0.1);
      height: 8px;
      border-radius: 4px;
      margin-bottom: 1.5rem;
      overflow: hidden;
    }

    .progress-bar {
      height: 100%;
      background: linear-gradient(90deg, var(--accent), var(--primary));
      border-radius: 4px;
      width: 0;
      transition: width 1s ease;
    }

    .rating-system {
      display: flex;
      justify-content: center;
      gap: 8px;
      margin-bottom: 1.8rem;
    }

    .star {
      color: #ddd;
      cursor: pointer;
      font-size: 1.8rem;
      transition: var(--transition);
    }

    .star:hover {
      transform: scale(1.2);
    }

    .star.active {
      color: gold;
      text-shadow: 0 0 10px rgba(255, 215, 0, 0.7);
    }

    .action-buttons {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 15px;
      margin-bottom: 1.5rem;
    }

    .action-btn {
      padding: 12px;
      border-radius: var(--radius-sm);
      border: none;
      background: rgba(138, 43, 226, 0.1);
      color: var(--primary);
      cursor: pointer;
      transition: var(--transition);
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      font-weight: 600;
    }

    .action-btn:hover {
      background: rgba(138, 43, 226, 0.2);
      transform: translateY(-3px);
    }

    .action-btn.liked {
      background: rgba(255, 0, 0, 0.15);
      color: var(--accent);
    }

    .comments-section {
      background: var(--bg-comment);
      border-radius: var(--radius-sm);
      padding: 1.5rem;
      margin-top: 1.5rem;
      border: 1px solid var(--border-color);
    }

    .comment-form {
      display: flex;
      gap: 15px;
      margin-bottom: 1.5rem;
    }

    .comment-input {
      flex: 1;
      padding: 15px;
      border-radius: var(--radius-sm);
      border: none;
      background: rgba(255, 255, 255, 0.08);
      color: var(--text-primary);
      font-size: 1rem;
    }

    .comment-input:focus {
      outline: 2px solid var(--primary);
    }

    .comment-list {
      max-height: 300px;
      overflow-y: auto;
      padding-right: 10px;
    }

    .comment {
      background: var(--bg-comment);
      border-radius: var(--radius-sm);
      padding: 15px;
      margin-bottom: 15px;
      animation: fadeIn 0.5s ease;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .comment-header {
      display: flex;
      justify-content: space-between;
      margin-bottom: 10px;
      align-items: center;
    }

    .comment-user {
      display: flex;
      align-items: center;
      gap: 10px;
      font-weight: 700;
    }

    .comment-user img {
      width: 32px;
      height: 32px;
      border-radius: 50%;
      object-fit: cover;
    }

    .comment-time {
      color: var(--text-secondary);
      font-size: 0.85rem;
    }

    .comment-content {
      line-height: 1.5;
    }

    .waveform {
      height: 100px;
      margin-bottom: 1.5rem;
      border-radius: var(--radius-sm);
      overflow: hidden;
    }

    /* AUDIO PLAYER */
    .audio-player {
      background: rgba(30, 30, 46, 0.7);
      border-radius: var(--radius);
      padding: 1.5rem;
      margin-top: 2rem;
      border: 1px solid var(--border-color);
    }

    .player-controls {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 1.5rem;
    }

    .player-btn {
      background: var(--primary);
      width: 50px;
      height: 50px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      border: none;
      color: white;
      cursor: pointer;
      transition: var(--transition);
    }

    .player-btn:hover {
      background: var(--accent);
      transform: scale(1.1);
    }

    .player-info {
      text-align: center;
    }

    .player-title {
      font-size: 1.4rem;
      font-weight: 700;
      margin-bottom: 5px;
    }

    .player-artist {
      color: var(--text-secondary);
      font-size: 1.1rem;
    }

    .progress-time {
      display: flex;
      justify-content: space-between;
      margin-bottom: 10px;
      color: var(--text-secondary);
    }

    .player-progress {
      width: 100%;
      height: 8px;
      background: rgba(255, 255, 255, 0.1);
      border-radius: 4px;
      cursor: pointer;
      position: relative;
    }

    .player-progress-bar {
      height: 100%;
      background: linear-gradient(90deg, var(--accent), var(--primary));
      border-radius: 4px;
      width: 0%;
    }

    /* FOOTER */
    footer {
      text-align: center;
      padding: 2.5rem;
      background: rgba(18, 18, 18, 0.9);
      margin-top: 5rem;
      border-top: 1px solid var(--border-color);
    }

    .social-links {
      display: flex;
      justify-content: center;
      gap: 20px;
      margin: 1.5rem 0;
    }

    .social-link {
      width: 50px;
      height: 50px;
      border-radius: 50%;
      background: rgba(255, 255, 255, 0.1);
      display: flex;
      align-items: center;
      justify-content: center;
      color: white;
      font-size: 1.5rem;
      transition: var(--transition);
    }

    .social-link:hover {
      background: var(--primary);
      transform: translateY(-5px);
    }

    .copyright {
      color: var(--text-secondary);
      margin-top: 1rem;
    }

    /* RESPONSIVIDADE */
    @media (max-width: 1200px) {
      .search-bar {
        width: 300px;
      }
    }

    @media (max-width: 992px) {
      .nav-links {
        display: none;
      }
      
      .search-bar {
        width: 200px;
      }
      
      .hero-section h2 {
        font-size: 2.8rem;
      }
    }

    @media (max-width: 768px) {
      header {
        flex-wrap: wrap;
        gap: 15px;
        padding: 1rem;
      }
      
      .search-bar {
        width: 100%;
        order: 3;
      }
      
      .user-actions {
        margin-left: auto;
      }
      
      .music-grid {
        grid-template-columns: 1fr;
      }
      
      .hero-section {
        padding: 3rem 1rem;
      }
      
      .hero-section h2 {
        font-size: 2.3rem;
      }
      
      .section-title {
        font-size: 1.8rem;
      }
    }
  </style>
</head>
<body>
  <header>
    <div class="logo">
      <i class="fas fa-wave-square logo-icon"></i>
      <h1>SoundVote</h1>
    </div>
    
    <nav class="nav-links">
      <a href="#" class="active"><i class="fas fa-home"></i> Início</a>
      <a href="#"><i class="fas fa-fire"></i> Em Alta</a>
      <a href="#"><i class="fas fa-headphones"></i> Gêneros</a>
      <a href="#"><i class="fas fa-calendar-star"></i> Lançamentos</a>
      <a href="#"><i class="fas fa-crown"></i> Premium</a>
    </nav>
    
    <div class="search-bar">
      <i class="fas fa-search"></i>
      <input type="text" placeholder="Buscar músicas, artistas...">
    </div>
    
    <div class="user-actions">
      <button class="btn btn-outline"><i class="fas fa-user-plus"></i> Registrar</button>
      <button class="btn btn-primary"><i class="fas fa-sign-in-alt"></i> Login</button>
      <button class="theme-switcher" id="themeToggle">
        <i class="fas fa-moon"></i>
      </button>
    </div>
  </header>

  <div class="main-container">
    <section class="hero-section">
      <h2>Vote nas músicas que movem o mundo</h2>
      <p>Descubra novos talentos, participe de rankings e defina as próximas tendências musicais</p>
      <button class="btn btn-primary" style="font-size: 1.2rem; padding: 15px 40px;">
        <i class="fas fa-vote-yea"></i> Começar a Votar
      </button>
    </section>
    
    <h2 class="section-title"><i class="fas fa-star"></i> Músicas em Destaque</h2>
    
    <div class="filters">
      <button class="filter-btn active">Todas</button>
      <button class="filter-btn">Pop</button>
      <button class="filter-btn">Rock</button>
      <button class="filter-btn">Hip Hop</button>
      <button class="filter-btn">Eletrônica</button>
      <button class="filter-btn">MPB</button>
      <button class="filter-btn">Sertanejo</button>
      <button class="filter-btn">Internacional</button>
    </div>
    
    <div class="music-grid">
      <!-- Música 1 -->
      <div class="music-card">
        <div class="card-header">
          <img src="https://source.unsplash.com/random/600x400/?music,night" alt="Blinding Lights" class="music-thumb">
          <div class="music-badge">#1 Trending</div>
          <button class="play-btn">
            <i class="fas fa-play"></i>
          </button>
        </div>
        
        <div class="card-body">
          <h3 class="music-title">Blinding Lights</h3>
          <p class="music-artist">
            <img src="https://source.unsplash.com/random/100x100/?portrait,man"> The Weeknd
          </p>
          
          <div class="waveform" id="waveform-1">
            <!-- Waveform will be generated here -->
          </div>
          
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
                <span class="comment-user">
                  <img src="https://source.unsplash.com/random/100x100/?portrait,woman"> Maria Silva
                </span>
                <span class="comment-time">2 horas atrás</span>
              </div>
              <p class="comment-content">Essa música nunca sai da minha playlist! Melhor do The Weeknd!</p>
            </div>
            
            <div class="comment">
              <div class="comment-header">
                <span class="comment-user">
                  <img src="https://source.unsplash.com/random/100x100/?portrait,man"> João Santos
                </span>
                <span class="comment-time">Ontem</span>
              </div>
              <p class="comment-content">Nostálgica demais, me lembra 2020!</p>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Música 2 -->
      <div class="music-card">
        <div class="card-header">
          <img src="https://source.unsplash.com/random/600x400/?music,concert" alt="Levitating" class="music-thumb">
          <div class="music-badge">#3 Trending</div>
          <button class="play-btn">
            <i class="fas fa-play"></i>
          </button>
        </div>
        
        <div class="card-body">
          <h3 class="music-title">Levitating</h3>
          <p class="music-artist">
            <img src="https://source.unsplash.com/random/100x100/?portrait,woman"> Dua Lipa
          </p>
          
          <div class="waveform" id="waveform-2">
            <!-- Waveform will be generated here -->
          </div>
          
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
          <div class="music-badge">Hot</div>
          <button class="play-btn">
            <i class="fas fa-play"></i>
          </button>
        </div>
        
        <div class="card-body">
          <h3 class="music-title">Peaches</h3>
          <p class="music-artist">
            <img src="https://source.unsplash.com/random/100x100/?portrait,man"> Justin Bieber
          </p>
          
          <div class="waveform" id="waveform-3">
            <!-- Waveform will be generated here -->
          </div>
          
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
      <h2 class="section-title"><i class="fas fa-chart-line"></i> Top 10 Global</h2>
      <div class="chart-container">
        <canvas id="trendingChart"></canvas>
      </div>
    </div>
  </div>

  <footer>
    <div class="logo">
      <i class="fas fa-wave-square logo-icon"></i>
      <h1>SoundVote</h1>
    </div>
    
    <p>A plataforma onde os fãs definem o sucesso</p>
    
    <div class="social-links">
      <a href="#" class="social-link"><i class="fab fa-facebook-f"></i></a>
      <a href="#" class="social-link"><i class="fab fa-twitter"></i></a>
      <a href="#" class="social-link"><i class="fab fa-instagram"></i></a>
      <a href="#" class="social-link"><i class="fab fa-youtube"></i></a>
      <a href="#" class="social-link"><i class="fab fa-spotify"></i></a>
    </div>
    
    <p class="copyright">Desenvolvido por Arthur 💚 | SoundVote &copy; 2025 - Todos os direitos reservados</p>
  </footer>

  <script>
    document.addEventListener('DOMContentLoaded', function() {
      // Theme Toggle
      const themeToggle = document.getElementById('themeToggle');
      const themeIcon = themeToggle.querySelector('i');
      const html = document.documentElement;
      
      function setTheme(isDark) {
        if (isDark) {
          html.setAttribute('data-theme', 'dark');
          themeIcon.classList.remove('fa-sun');
          themeIcon.classList.add('fa-moon');
          localStorage.setItem('theme', 'dark');
        } else {
          html.setAttribute('data-theme', 'light');
          themeIcon.classList.remove('fa-moon');
          themeIcon.classList.add('fa-sun');
          localStorage.setItem('theme', 'light');
        }
      }
      
      // Initial theme
      const savedTheme = localStorage.getItem('theme') || 'dark';
      setTheme(savedTheme === 'dark');
      
      themeToggle.addEventListener('click', () => {
        const isDark = html.getAttribute('data-theme') === 'dark';
        setTheme(!isDark);
      });

      // Like System
      const likeButtons = document.querySelectorAll('.like-btn');
      likeButtons.forEach(button => {
        button.addEventListener('click', function() {
          const musicId = this.getAttribute('data-id');
          this.classList.toggle('liked');
          const icon = this.querySelector('i');
          
          if (this.classList.contains('liked')) {
            this.innerHTML = `<i class="fas fa-heart"></i> Curtido`;
            // Sound effect
            playSound('like');
            // Animation
            gsap.to(this, { scale: 1.2, duration: 0.2, yoyo: true, repeat: 1 });
            // Save
            localStorage.setItem(`music_${musicId}_liked`, 'true');
          } else {
            this.innerHTML = `<i class="far fa-heart"></i> Curtir`;
            // Save
            localStorage.removeItem(`music_${musicId}_liked`);
          }
        });
      });

      // Star Rating System
      const starRatings = document.querySelectorAll('.rating-system');
      starRatings.forEach(ratingSystem => {
        const stars = ratingSystem.querySelectorAll('.star');
        stars.forEach(star => {
          star.addEventListener('click', function() {
            const value = this.getAttribute('data-value');
            const musicId = this.closest('.music-card').querySelector('.like-btn').getAttribute('data-id');
            
            // Update stars UI
            stars.forEach((s, index) => {
              if (index < value) {
                s.innerHTML = '<i class="fas fa-star"></i>';
                s.classList.add('active');
              } else {
                s.innerHTML = '<i class="far fa-star"></i>';
                s.classList.remove('active');
              }
            });
            
            // Play sound
            playSound('star');
            
            // Animation
            gsap.fromTo(this, 
              { scale: 1 },
              { scale: 1.5, duration: 0.3, yoyo: true, repeat: 1 }
            );
            
            // Save rating
            localStorage.setItem(`music_${musicId}_rating`, value);
          });
        });
      });

      // Play Button Animation
      const playButtons = document.querySelectorAll('.play-btn');
      playButtons.forEach(button => {
        button.addEventListener('click', function() {
          const icon = this.querySelector('i');
          if (icon.classList.contains('fa-play')) {
            icon.classList.remove('fa-play');
            icon.classList.add('fa-pause');
            playSound('play');
          } else {
            icon.classList.remove('fa-pause');
            icon.classList.add('fa-play');
            playSound('pause');
          }
          
          // Animation
          gsap.to(this, { 
            scale: 0.9, 
            duration: 0.1,
            yoyo: true,
            repeat: 1
          });
        });
      });

      // Comment Submission
      const commentForms = document.querySelectorAll('.comment-form');
      commentForms.forEach(form => {
        const input = form.querySelector('.comment-input');
        const button = form.querySelector('.action-btn');
        const commentList = form.nextElementSibling;
        
        button.addEventListener('click', () => {
          if (input.value.trim() !== '') {
            const comment = createComment('Você', input.value);
            commentList.prepend(comment);
            input.value = '';
            playSound('comment');
          }
        });
        
        input.addEventListener('keypress', (e) => {
          if (e.key === 'Enter') {
            button.click();
          }
        });
      });

      function createComment(user, content) {
        const comment = document.createElement('div');
        comment.className = 'comment';
        comment.innerHTML = `
          <div class="comment-header">
            <span class="comment-user">
              <img src="https://source.unsplash.com/random/100x100/?portrait"> ${user}
            </span>
            <span class="comment-time">Agora mesmo</span>
          </div>
          <p class="comment-content">${content}</p>
        `;
        return comment;
      }

      // Load saved state
      function loadSavedState() {
        likeButtons.forEach(button => {
          const musicId = button.getAttribute('data-id');
          if (localStorage.getItem(`music_${musicId}_liked`) === 'true') {
            button.classList.add('liked');
            button.innerHTML = `<i class="fas fa-heart"></i> Curtido`;
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

      // Sound effects
      function playSound(type) {
        const audio = new Audio();
        audio.volume = 0.3;
        
        switch(type) {
          case 'like':
            audio.src = 'https://assets.mixkit.co/sfx/preview/mixkit-unlock-game-notification-253.mp3';
            break;
          case 'star':
            audio.src = 'https://assets.mixkit.co/sfx/preview/mixkit-magic-sparkles-300.mp3';
            break;
          case 'comment':
            audio.src = 'https://assets.mixkit.co/sfx/preview/mixkit-select-click-1109.mp3';
            break;
          case 'play':
            audio.src = 'https://assets.mixkit.co/sfx/preview/mixkit-select-click-1109.mp3';
            break;
          case 'pause':
            audio.src = 'https://assets.mixkit.co/sfx/preview/mixkit-unlock-game-notification-253.mp3';
            break;
        }
        
        audio.play().catch(e => console.log("Audio play failed:", e));
      }

      // Initialize Chart
      const ctx = document.getElementById('trendingChart').getContext('2d');
      new Chart(ctx, {
        type: 'bar',
        data: {
          labels: ['Blinding Lights', 'Levitating', 'Peaches', 'Stay', 'Good 4 U', 'Montero', 'Save Your Tears', 'Kiss Me More', 'Butter', 'Industry Baby'],
          datasets: [{
            label: 'Votos (milhares)',
            data: [245, 187, 156, 132, 128, 118, 112, 98, 87, 82],
            backgroundColor: [
              'rgba(138, 43, 226, 0.7)',
              'rgba(255, 107, 107, 0.7)',
              'rgba(75, 0, 130, 0.7)',
              'rgba(138, 43, 226, 0.5)',
              'rgba(255, 107, 107, 0.5)',
              'rgba(75, 0, 130, 0.5)',
              'rgba(138, 43, 226, 0.3)',
              'rgba(255, 107, 107, 0.3)',
              'rgba(75, 0, 130, 0.3)',
              'rgba(138, 43, 226, 0.2)'
            ],
            borderColor: 'rgba(255, 255, 255, 0.3)',
            borderWidth: 1
          }]
        },
        options: {
          responsive: true,
          plugins: {
            legend: {
              display: false
            }
          },
          scales: {
            y: {
              beginAtZero: true,
              grid: {
                color: 'rgba(255, 255, 255, 0.1)'
              },
              ticks: {
                color: 'rgba(255, 255, 255, 0.7)'
              }
            },
            x: {
              grid: {
                display: false
              },
              ticks: {
                color: 'rgba(255, 255, 255, 0.7)'
              }
            }
          }
        }
      });

      // Progress bars animation
      gsap.to('.progress-bar', {
        width: '100%',
        duration: 2,
        ease: 'power2.out',
        stagger: 0.2
      });

      loadSavedState();
    });
  </script>
</body>
</html>
