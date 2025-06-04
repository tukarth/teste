<!DOCTYPE html>
<html lang="pt-BR" data-theme="auto">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>🎧 SoundVote - Plataforma Musical Interativa</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/wavesurfer.js/7.0.0/wavesurfer.min.css">
  <script src="https://cdnjs.cloudflare.com/ajax/libs/wavesurfer.js/7.0.0/wavesurfer.min.js"></script>
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
      --transition-slow: all 0.6s cubic-bezier(0.16, 1, 0.3, 1);
      --shadow: 0 10px 25px rgba(0,0,0,0.2);
      --shadow-hover: 0 15px 35px rgba(138, 43, 226, 0.25);
      --radius: 16px;
      --radius-sm: 8px;
    }

    .dark-theme {
      --bg-primary: var(--dark);
      --bg-secondary: var(--darker);
      --bg-card: rgba(30, 30, 46, 0.6);
      --bg-card-hover: rgba(50, 50, 70, 0.7);
      --bg-input: rgba(255, 255, 255, 0.08);
      --text-primary: var(--light);
      --text-secondary: #ccc;
      --text-tertiary: #999;
      --border-color: rgba(255,255,255,0.1);
      --hover-bg: rgba(255,255,255,0.05);
    }

    .light-theme {
      --bg-primary: #f0f2f5;
      --bg-secondary: #ffffff;
      --bg-card: rgba(255, 255, 255, 0.8);
      --bg-card-hover: rgba(255, 255, 255, 0.95);
      --bg-input: rgba(0, 0, 0, 0.05);
      --text-primary: var(--text-dark);
      --text-secondary: #555;
      --text-tertiary: #777;
      --border-color: rgba(0,0,0,0.1);
      --hover-bg: rgba(0,0,0,0.02);
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    body {
      background: var(--bg-primary);
      color: var(--text-primary);
      min-height: 100vh;
      line-height: 1.6;
      overflow-x: hidden;
    }

    /* ======= Header & Navigation ======= */
    .app-header {
      background: var(--bg-secondary);
      backdrop-filter: blur(12px);
      -webkit-backdrop-filter: blur(12px);
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

    .logo-container {
      display: flex;
      align-items: center;
      gap: 12px;
    }

    .logo {
      width: 40px;
      height: 40px;
      background: linear-gradient(135deg, var(--primary), var(--accent));
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
    }

    .logo i {
      color: white;
      font-size: 1.2rem;
    }

    .brand {
      font-size: 1.8rem;
      font-weight: 700;
      background: linear-gradient(90deg, var(--primary), var(--accent));
      -webkit-background-clip: text;
      background-clip: text;
      color: transparent;
    }

    .nav-container {
      display: flex;
      gap: 2rem;
    }

    .nav-link {
      color: var(--text-primary);
      text-decoration: none;
      font-weight: 500;
      font-size: 1.1rem;
      transition: var(--transition);
      display: flex;
      align-items: center;
      gap: 8px;
      padding: 8px 16px;
      border-radius: var(--radius-sm);
    }

    .nav-link:hover, .nav-link.active {
      background: var(--hover-bg);
      color: var(--primary);
    }

    .search-container {
      position: relative;
      width: 35%;
    }

    .search-bar {
      width: 100%;
      padding: 12px 20px;
      background: var(--bg-input);
      border: 1px solid var(--border-color);
      border-radius: 50px;
      color: var(--text-primary);
      font-size: 1rem;
      transition: var(--transition);
    }

    .search-bar:focus {
      outline: none;
      border-color: var(--primary);
      box-shadow: 0 0 0 3px rgba(138, 43, 226, 0.2);
    }

    .user-actions {
      display: flex;
      align-items: center;
      gap: 1rem;
    }

    .theme-toggle {
      background: var(--bg-input);
      border: none;
      width: 40px;
      height: 40px;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      cursor: pointer;
      transition: var(--transition);
      color: var(--text-primary);
    }

    .theme-toggle:hover {
      background: var(--hover-bg);
      transform: rotate(20deg);
    }

    .btn {
      padding: 12px 28px;
      border-radius: 50px;
      border: none;
      font-weight: 600;
      font-size: 1rem;
      cursor: pointer;
      transition: var(--transition);
      display: inline-flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
    }

    .btn-primary {
      background: linear-gradient(to right, var(--primary), var(--accent));
      color: white;
    }

    .btn-outline {
      background: transparent;
      border: 2px solid var(--primary);
      color: var(--primary);
    }

    .btn:hover {
      transform: translateY(-3px);
      box-shadow: var(--shadow-hover);
    }

    .btn-primary:hover {
      background: linear-gradient(to right, var(--primary-dark), var(--accent-dark));
    }

    .btn-outline:hover {
      background: rgba(138, 43, 226, 0.1);
    }

    /* ======= Main Layout ======= */
    .app-container {
      display: grid;
      grid-template-columns: 240px 1fr;
      max-width: 1600px;
      margin: 0 auto;
      padding: 2rem;
      gap: 2rem;
    }

    .sidebar {
      background: var(--bg-card);
      border-radius: var(--radius);
      padding: 1.5rem;
      height: fit-content;
      box-shadow: var(--shadow);
    }

    .sidebar-section {
      margin-bottom: 2rem;
    }

    .sidebar-title {
      font-size: 1.1rem;
      margin-bottom: 1rem;
      color: var(--text-secondary);
      text-transform: uppercase;
      letter-spacing: 1px;
    }

    .sidebar-menu {
      list-style: none;
    }

    .sidebar-menu li {
      margin-bottom: 0.8rem;
    }

    .sidebar-menu a {
      display: flex;
      align-items: center;
      gap: 12px;
      color: var(--text-primary);
      text-decoration: none;
      padding: 10px 12px;
      border-radius: var(--radius-sm);
      transition: var(--transition);
    }

    .sidebar-menu a:hover, .sidebar-menu a.active {
      background: var(--hover-bg);
      color: var(--primary);
    }

    .main-content {
      display: flex;
      flex-direction: column;
      gap: 2rem;
    }

    /* ======= Music Player ======= */
    .player-container {
      position: fixed;
      bottom: 0;
      left: 0;
      width: 100%;
      background: var(--bg-secondary);
      border-top: 1px solid var(--border-color);
      padding: 1rem 2rem;
      box-shadow: 0 -5px 25px rgba(0,0,0,0.1);
      z-index: 1000;
    }

    .player-grid {
      display: grid;
      grid-template-columns: 300px 1fr 300px;
      gap: 2rem;
      align-items: center;
    }

    .current-track {
      display: flex;
      align-items: center;
      gap: 1rem;
    }

    .track-thumb {
      width: 60px;
      height: 60px;
      border-radius: 8px;
      object-fit: cover;
      box-shadow: var(--shadow);
    }

    .track-info {
      display: flex;
      flex-direction: column;
    }

    .track-title {
      font-weight: 600;
      font-size: 1.1rem;
    }

    .track-artist {
      color: var(--text-secondary);
      font-size: 0.9rem;
    }

    .player-controls {
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 1rem;
    }

    .control-buttons {
      display: flex;
      align-items: center;
      gap: 1.5rem;
    }

    .control-btn {
      background: transparent;
      border: none;
      color: var(--text-primary);
      font-size: 1.2rem;
      cursor: pointer;
      transition: var(--transition);
      display: flex;
      align-items: center;
      justify-content: center;
      width: 40px;
      height: 40px;
    }

    .control-btn:hover {
      color: var(--primary);
      transform: scale(1.1);
    }

    .play-btn {
      background: var(--primary);
      color: white;
      border-radius: 50%;
      width: 50px;
      height: 50px;
      font-size: 1.4rem;
    }

    .play-btn:hover {
      background: var(--primary-dark);
      transform: scale(1.05);
    }

    .progress-container {
      width: 100%;
      display: flex;
      align-items: center;
      gap: 1rem;
    }

    .progress-time {
      color: var(--text-secondary);
      font-size: 0.9rem;
      min-width: 40px;
    }

    .progress-bar {
      flex: 1;
      height: 6px;
      background: var(--bg-input);
      border-radius: 3px;
      cursor: pointer;
      position: relative;
    }

    .progress-fill {
      height: 100%;
      background: linear-gradient(to right, var(--primary), var(--accent));
      border-radius: 3px;
      width: 30%;
    }

    .waveform-container {
      height: 80px;
      width: 100%;
      cursor: pointer;
    }

    .extra-controls {
      display: flex;
      justify-content: flex-end;
      gap: 1rem;
    }

    .volume-container {
      display: flex;
      align-items: center;
      gap: 8px;
    }

    /* ======= Music Grid ======= */
    .section-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 1.5rem;
    }

    .section-title {
      font-size: 1.8rem;
      font-weight: 700;
    }

    .view-all {
      color: var(--primary);
      text-decoration: none;
      font-weight: 600;
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .music-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
      gap: 2rem;
      margin-bottom: 3rem;
    }

    .music-card {
      background: var(--bg-card);
      border-radius: var(--radius);
      overflow: hidden;
      transition: var(--transition);
      position: relative;
      box-shadow: var(--shadow);
    }

    .music-card:hover {
      transform: translateY(-10px);
      box-shadow: var(--shadow-hover);
    }

    .card-media {
      position: relative;
    }

    .music-thumb {
      width: 100%;
      height: 200px;
      object-fit: cover;
    }

    .overlay {
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: rgba(0,0,0,0.5);
      display: flex;
      align-items: center;
      justify-content: center;
      opacity: 0;
      transition: var(--transition);
    }

    .music-card:hover .overlay {
      opacity: 1;
    }

    .card-play-btn {
      width: 60px;
      height: 60px;
      background: var(--primary);
      color: white;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      font-size: 1.8rem;
      cursor: pointer;
      transition: var(--transition);
      transform: translateY(10px);
    }

    .music-card:hover .card-play-btn {
      transform: translateY(0);
    }

    .card-body {
      padding: 1.5rem;
    }

    .music-title {
      font-size: 1.3rem;
      font-weight: 700;
      margin-bottom: 0.5rem;
      display: -webkit-box;
      -webkit-line-clamp: 1;
      -webkit-box-orient: vertical;
      overflow: hidden;
    }

    .music-artist {
      color: var(--text-secondary);
      font-size: 1rem;
      margin-bottom: 1.2rem;
    }

    .music-stats {
      display: flex;
      justify-content: space-between;
      margin-bottom: 1.2rem;
    }

    .stat-item {
      display: flex;
      align-items: center;
      gap: 5px;
      color: var(--text-secondary);
      font-size: 0.9rem;
    }

    .action-buttons {
      display: flex;
      gap: 10px;
    }

    .action-btn {
      flex: 1;
      padding: 10px;
      border-radius: var(--radius-sm);
      border: none;
      background: var(--bg-input);
      color: var(--text-primary);
      cursor: pointer;
      transition: var(--transition);
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
    }

    .action-btn:hover {
      background: var(--hover-bg);
      color: var(--primary);
    }

    .action-btn.liked {
      background: rgba(255, 0, 0, 0.15);
      color: #ff6b6b;
    }

    .badge {
      position: absolute;
      top: 15px;
      right: 15px;
      background: var(--accent);
      color: white;
      padding: 5px 12px;
      border-radius: 30px;
      font-size: 0.8rem;
      font-weight: 600;
    }

    /* ======= Community Features ======= */
    .comments-section {
      background: var(--bg-card);
      border-radius: var(--radius);
      padding: 1.5rem;
      margin-top: 1.5rem;
    }

    .comment-form {
      display: flex;
      gap: 10px;
      margin-bottom: 1.5rem;
    }

    .comment-input {
      flex: 1;
      padding: 12px 20px;
      border-radius: 50px;
      border: none;
      background: var(--bg-input);
      color: var(--text-primary);
      font-size: 1rem;
    }

    .comment-list {
      max-height: 300px;
      overflow-y: auto;
    }

    .comment {
      background: var(--bg-input);
      border-radius: var(--radius-sm);
      padding: 12px;
      margin-bottom: 12px;
    }

    .comment-header {
      display: flex;
      justify-content: space-between;
      margin-bottom: 8px;
    }

    .comment-user {
      font-weight: 700;
      color: var(--primary);
    }

    .comment-time {
      color: var(--text-tertiary);
      font-size: 0.9rem;
    }

    /* ======= Advanced Features ======= */
    .playlist-grid {
      display: grid;
      grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
      gap: 1.5rem;
    }

    .playlist-card {
      background: var(--bg-card);
      border-radius: var(--radius);
      overflow: hidden;
      transition: var(--transition);
      box-shadow: var(--shadow);
    }

    .playlist-card:hover {
      transform: translateY(-5px);
      box-shadow: var(--shadow-hover);
    }

    .playlist-header {
      position: relative;
      height: 140px;
    }

    .playlist-thumb {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }

    .playlist-overlay {
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background: rgba(138, 43, 226, 0.7);
      display: flex;
      align-items: center;
      justify-content: center;
      opacity: 0;
      transition: var(--transition);
    }

    .playlist-card:hover .playlist-overlay {
      opacity: 1;
    }

    .playlist-body {
      padding: 1rem;
    }

    .playlist-title {
      font-weight: 600;
      margin-bottom: 0.5rem;
    }

    .playlist-stats {
      color: var(--text-secondary);
      font-size: 0.9rem;
    }

    .trending-chart {
      background: var(--bg-card);
      border-radius: var(--radius);
      padding: 2rem;
      box-shadow: var(--shadow);
    }

    .chart-container {
      height: 300px;
      margin-top: 1.5rem;
    }

    /* ======= Animations ======= */
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(20px); }
      to { opacity: 1; transform: translateY(0); }
    }

    .animate-in {
      animation: fadeIn 0.6s ease-out forwards;
    }

    /* ======= Responsive Design ======= */
    @media (max-width: 1200px) {
      .app-container {
        grid-template-columns: 200px 1fr;
      }

      .player-grid {
        grid-template-columns: 200px 1fr 200px;
      }
    }

    @media (max-width: 992px) {
      .app-container {
        grid-template-columns: 1fr;
      }

      .sidebar {
        display: none;
      }

      .player-grid {
        grid-template-columns: 1fr;
        gap: 1rem;
      }

      .extra-controls {
        justify-content: center;
      }
    }

    @media (max-width: 768px) {
      .app-header {
        flex-wrap: wrap;
        gap: 1rem;
        padding: 1rem;
      }

      .nav-container {
        order: 3;
        width: 100%;
        justify-content: center;
      }

      .search-container {
        order: 2;
        width: 100%;
      }

      .user-actions {
        margin-left: auto;
      }

      .music-grid {
        grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
      }
    }
  </style>
</head>
<body>
  <!-- Top Navigation -->
  <header class="app-header">
    <div class="logo-container">
      <div class="logo">
        <i class="fas fa-music"></i>
      </div>
      <div class="brand">SoundVote</div>
    </div>

    <nav class="nav-container">
      <a href="#" class="nav-link active"><i class="fas fa-home"></i> Início</a>
      <a href="#" class="nav-link"><i class="fas fa-compass"></i> Descobrir</a>
      <a href="#" class="nav-link"><i class="fas fa-chart-line"></i> Rankings</a>
      <a href="#" class="nav-link"><i class="fas fa-calendar-star"></i> Eventos</a>
    </nav>

    <div class="search-container">
      <input type="text" class="search-bar" placeholder="Buscar músicas, artistas, playlists...">
    </div>

    <div class="user-actions">
      <button class="theme-toggle" id="themeToggle">
        <i class="fas fa-moon"></i>
      </button>
      <button class="btn btn-outline"><i class="fas fa-user-plus"></i> Registrar</button>
      <button class="btn btn-primary"><i class="fas fa-sign-in-alt"></i> Login</button>
    </div>
  </header>

  <!-- Main Content -->
  <div class="app-container">
    <!-- Sidebar -->
    <aside class="sidebar">
      <div class="sidebar-section">
        <h3 class="sidebar-title">Biblioteca</h3>
        <ul class="sidebar-menu">
          <li><a href="#" class="active"><i class="fas fa-heart"></i> Músicas Curtidas</a></li>
          <li><a href="#"><i class="fas fa-history"></i> Tocadas Recentemente</a></li>
          <li><a href="#"><i class="fas fa-play-circle"></i> Suas Playlists</a></li>
          <li><a href="#"><i class="fas fa-microphone-alt"></i> Seus Artistas</a></li>
          <li><a href="#"><i class="fas fa-folder"></i> Álbuns Salvos</a></li>
        </ul>
      </div>

      <div class="sidebar-section">
        <h3 class="sidebar-title">Playlists</h3>
        <ul class="sidebar-menu">
          <li><a href="#"><i class="fas fa-fire"></i> Top Brasil</a></li>
          <li><a href="#"><i class="fas fa-globe-americas"></i> Global Hits</a></li>
          <li><a href="#"><i class="fas fa-wind"></i> Chill Vibes</a></li>
          <li><a href="#"><i class="fas fa-running"></i> Workout Hits</a></li>
          <li><a href="#"><i class="fas fa-cloud-moon"></i> Sleep Essentials</a></li>
        </ul>
      </div>

      <div class="sidebar-section">
        <h3 class="sidebar-title">Gêneros</h3>
        <ul class="sidebar-menu">
          <li><a href="#"><i class="fas fa-guitar"></i> Rock</a></li>
          <li><a href="#"><i class="fas fa-hiphop"></i> Hip Hop</a></li>
          <li><a href="#"><i class="fas fa-microphone"></i> Pop</a></li>
          <li><a href="#"><i class="fas fa-headphones"></i> Eletrônica</a></li>
          <li><a href="#"><i class="fas fa-drum"></i> Sertanejo</a></li>
        </ul>
      </div>
    </aside>

    <!-- Main Content Area -->
    <main class="main-content">
      <!-- Featured Section -->
      <section class="music-section">
        <div class="section-header">
          <h2 class="section-title">Músicas em Destaque</h2>
          <a href="#" class="view-all">Ver tudo <i class="fas fa-chevron-right"></i></a>
        </div>

        <div class="music-grid">
          <!-- Music Card 1 -->
          <div class="music-card animate-in">
            <div class="card-media">
              <img src="https://source.unsplash.com/random/600x400/?music,concert" alt="Blinding Lights" class="music-thumb">
              <div class="overlay">
                <div class="card-play-btn">
                  <i class="fas fa-play"></i>
                </div>
              </div>
              <div class="badge">Trending</div>
            </div>
            <div class="card-body">
              <h3 class="music-title">Blinding Lights</h3>
              <p class="music-artist">The Weeknd</p>
              
              <div class="music-stats">
                <div class="stat-item">
                  <i class="fas fa-play-circle"></i> 245M
                </div>
                <div class="stat-item">
                  <i class="fas fa-heart"></i> 12.4M
                </div>
                <div class="stat-item">
                  <i class="fas fa-clock"></i> 3:22
                </div>
              </div>
              
              <div class="action-buttons">
                <button class="action-btn like-btn" data-id="1">
                  <i class="far fa-heart"></i> Curtir
                </button>
                <button class="action-btn">
                  <i class="fas fa-plus"></i> Playlist
                </button>
              </div>
            </div>
          </div>
          
          <!-- Music Card 2 -->
          <div class="music-card animate-in" style="animation-delay: 0.1s">
            <div class="card-media">
              <img src="https://source.unsplash.com/random/600x400/?music,performance" alt="Levitating" class="music-thumb">
              <div class="overlay">
                <div class="card-play-btn">
                  <i class="fas fa-play"></i>
                </div>
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
                  <i class="fas fa-heart"></i> 9.8M
                </div>
                <div class="stat-item">
                  <i class="fas fa-clock"></i> 3:45
                </div>
              </div>
              
              <div class="action-buttons">
                <button class="action-btn like-btn" data-id="2">
                  <i class="far fa-heart"></i> Curtir
                </button>
                <button class="action-btn">
                  <i class="fas fa-plus"></i> Playlist
                </button>
              </div>
            </div>
          </div>
          
          <!-- Music Card 3 -->
          <div class="music-card animate-in" style="animation-delay: 0.2s">
            <div class="card-media">
              <img src="https://source.unsplash.com/random/600x400/?music,band" alt="Peaches" class="music-thumb">
              <div class="overlay">
                <div class="card-play-btn">
                  <i class="fas fa-play"></i>
                </div>
              </div>
              <div class="badge">New</div>
            </div>
            <div class="card-body">
              <h3 class="music-title">Peaches</h3>
              <p class="music-artist">Justin Bieber ft. Daniel Caesar</p>
              
              <div class="music-stats">
                <div class="stat-item">
                  <i class="fas fa-play-circle"></i> 156M
                </div>
                <div class="stat-item">
                  <i class="fas fa-heart"></i> 8.3M
                </div>
                <div class="stat-item">
                  <i class="fas fa-clock"></i> 3:18
                </div>
              </div>
              
              <div class="action-buttons">
                <button class="action-btn like-btn" data-id="3">
                  <i class="far fa-heart"></i> Curtir
                </button>
                <button class="action-btn">
                  <i class="fas fa-plus"></i> Playlist
                </button>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Trending Chart -->
      <section class="trending-chart">
        <div class="section-header">
          <h2 class="section-title">Top 10 Global</h2>
          <a href="#" class="view-all">Ver ranking completo <i class="fas fa-chevron-right"></i></a>
        </div>
        <div class="chart-container">
          <canvas id="trendChart"></canvas>
        </div>
      </section>

      <!-- Community Section -->
      <section class="community-section">
        <div class="section-header">
          <h2 class="section-title">Comunidade</h2>
        </div>
        
        <div class="music-card">
          <div class="card-body">
            <h3 class="music-title">Blinding Lights - The Weeknd</h3>
            <p class="music-artist">O que a comunidade está dizendo:</p>
            
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
                  <p>Essa música nunca sai da minha playlist! Melhor do The Weeknd! 🎧🔥</p>
                </div>
                
                <div class="comment">
                  <div class="comment-header">
                    <span class="comment-user">João Santos</span>
                    <span class="comment-time">Ontem</span>
                  </div>
                  <p>Nostálgica demais, me lembra 2020! Queria que essa música nunca acabasse.</p>
                </div>
                
                <div class="comment">
                  <div class="comment-header">
                    <span class="comment-user">Ana Beatriz</span>
                    <span class="comment-time">3 dias atrás</span>
                  </div>
                  <p>Alguém mais acha que o refrão é hipnotizante? Não consigo parar de ouvir!</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </main>
  </div>

  <!-- Music Player -->
  <div class="player-container">
    <div class="player-grid">
      <div class="current-track">
        <img src="https://source.unsplash.com/random/100x100/?album" alt="Album Cover" class="track-thumb">
        <div class="track-info">
          <div class="track-title">Blinding Lights</div>
          <div class="track-artist">The Weeknd</div>
        </div>
        <button class="action-btn">
          <i class="far fa-heart"></i>
        </button>
      </div>
      
      <div class="player-controls">
        <div class="control-buttons">
          <button class="control-btn">
            <i class="fas fa-random"></i>
          </button>
          <button class="control-btn">
            <i class="fas fa-step-backward"></i>
          </button>
          <button class="control-btn play-btn">
            <i class="fas fa-play"></i>
          </button>
          <button class="control-btn">
            <i class="fas fa-step-forward"></i>
          </button>
          <button class="control-btn">
            <i class="fas fa-repeat"></i>
          </button>
        </div>
        
        <div class="progress-container">
          <div class="progress-time">0:00</div>
          <div class="progress-bar">
            <div class="progress-fill"></div>
          </div>
          <div class="progress-time">3:22</div>
        </div>
      </div>
      
      <div class="extra-controls">
        <div class="volume-container">
          <button class="control-btn">
            <i class="fas fa-volume-up"></i>
          </button>
          <div class="progress-bar" style="width: 100px">
            <div class="progress-fill" style="width: 70%"></div>
          </div>
        </div>
        <button class="control-btn">
          <i class="fas fa-list"></i>
        </button>
      </div>
    </div>
  </div>

  <script>
    // ====== Theme Management ======
    const themeToggle = document.getElementById('themeToggle');
    const themeIcon = themeToggle.querySelector('i');
    
    function initTheme() {
      const savedTheme = localStorage.getItem('theme');
      const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
      
      if (savedTheme === 'dark' || (!savedTheme && prefersDark)) {
        document.documentElement.classList.add('dark-theme');
        themeIcon.classList.remove('fa-moon');
        themeIcon.classList.add('fa-sun');
      } else {
        document.documentElement.classList.add('light-theme');
        themeIcon.classList.remove('fa-sun');
        themeIcon.classList.add('fa-moon');
      }
    }
    
    function toggleTheme() {
      if (document.documentElement.classList.contains('dark-theme')) {
        document.documentElement.classList.remove('dark-theme');
        document.documentElement.classList.add('light-theme');
        localStorage.setItem('theme', 'light');
        themeIcon.classList.remove('fa-sun');
        themeIcon.classList.add('fa-moon');
      } else {
        document.documentElement.classList.remove('light-theme');
        document.documentElement.classList.add('dark-theme');
        localStorage.setItem('theme', 'dark');
        themeIcon.classList.remove('fa-moon');
        themeIcon.classList.add('fa-sun');
      }
    }
    
    themeToggle.addEventListener('click', toggleTheme);
    
    // ====== Player Functionality ======
    const playBtn = document.querySelector('.play-btn');
    const progressFill = document.querySelector('.progress-fill');
    const progressBar = document.querySelector('.progress-bar');
    const currentTimeEl = document.querySelector('.progress-time:first-child');
    const durationEl = document.querySelector('.progress-time:last-child');
    
    let isPlaying = false;
    
    playBtn.addEventListener('click', function() {
      isPlaying = !isPlaying;
      const icon = playBtn.querySelector('i');
      
      if (isPlaying) {
        icon.classList.remove('fa-play');
        icon.classList.add('fa-pause');
        // Iniciar a música aqui
      } else {
        icon.classList.remove('fa-pause');
        icon.classList.add('fa-play');
        // Pausar a música aqui
      }
    });
    
    // ====== Chart Initialization ======
    const ctx = document.getElementById('trendChart').getContext('2d');
    const trendChart = new Chart(ctx, {
      type: 'bar',
      data: {
        labels: ['Blinding Lights', 'Levitating', 'Peaches', 'Save Your Tears', 'Stay', 'Good 4 U', 'Montero', 'Kiss Me More', 'Butter', 'Industry Baby'],
        datasets: [{
          label: 'Votos',
          data: [245, 187, 156, 142, 138, 125, 118, 110, 102, 98],
          backgroundColor: [
            'rgba(138, 43, 226, 0.7)',
            'rgba(255, 107, 107, 0.7)',
            'rgba(74, 194, 107, 0.7)',
            'rgba(75, 0, 130, 0.7)',
            'rgba(255, 159, 64, 0.7)',
            'rgba(153, 102, 255, 0.7)',
            'rgba(54, 162, 235, 0.7)',
            'rgba(255, 99, 132, 0.7)',
            'rgba(255, 206, 86, 0.7)',
            'rgba(75, 192, 192, 0.7)'
          ],
          borderColor: [
            'rgba(138, 43, 226, 1)',
            'rgba(255, 107, 107, 1)',
            'rgba(74, 194, 107, 1)',
            'rgba(75, 0, 130, 1)',
            'rgba(255, 159, 64, 1)',
            'rgba(153, 102, 255, 1)',
            'rgba(54, 162, 235, 1)',
            'rgba(255, 99, 132, 1)',
            'rgba(255, 206, 86, 1)',
            'rgba(75, 192, 192, 1)'
          ],
          borderWidth: 1
        }]
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
        plugins: {
          legend: {
            display: false
          },
          title: {
            display: true,
            text: 'Músicas Mais Votadas (em milhões)',
            color: 'var(--text-primary)',
            font: {
              size: 16
            }
          }
        },
        scales: {
          y: {
            beginAtZero: true,
            grid: {
              color: 'rgba(255,255,255,0.1)'
            },
            ticks: {
              color: 'var(--text-secondary)'
            }
          },
          x: {
            grid: {
              display: false
            },
            ticks: {
              color: 'var(--text-secondary)',
              maxRotation: 45,
              minRotation: 45
            }
          }
        }
      }
    });
    
    // ====== Like System ======
    const likeButtons = document.querySelectorAll('.like-btn');
    
    likeButtons.forEach(button => {
      button.addEventListener('click', function() {
        const musicId = this.getAttribute('data-id');
        const icon = this.querySelector('i');
        
        if (icon.classList.contains('far')) {
          icon.classList.remove('far');
          icon.classList.add('fas');
          this.innerHTML = `<i class="fas fa-heart"></i> Curtido`;
          this.classList.add('liked');
          localStorage.setItem(`music_${musicId}_liked`, 'true');
        } else {
          icon.classList.remove('fas');
          icon.classList.add('far');
          this.innerHTML = `<i class="far fa-heart"></i> Curtir`;
          this.classList.remove('liked');
          localStorage.removeItem(`music_${musicId}_liked`);
        }
      });
    });
    
    // ====== Card Play Buttons ======
    const cardPlayBtns = document.querySelectorAll('.card-play-btn');
    
    cardPlayBtns.forEach(btn => {
      btn.addEventListener('click', function() {
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
    
    // ====== Initialize ======
    document.addEventListener('DOMContentLoaded', function() {
      initTheme();
      
      // Load liked status
      likeButtons.forEach(button => {
        const musicId = button.getAttribute('data-id');
        if (localStorage.getItem(`music_${musicId}_liked`) === 'true') {
          button.innerHTML = `<i class="fas fa-heart"></i> Curtido`;
          button.classList.add('liked');
        }
      });
    });
  </script>
</body>
</html>
