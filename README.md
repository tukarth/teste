<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>SoundVote</title>
    <style>
        :root {
            --bg-primary: #121212;
            --text-primary: #ffffff;
            --accent-color: #1DB954;
            --secondary-color: #282828;
        }
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            font-family: 'Arial', sans-serif;
            background-color: var(--bg-primary);
            color: var(--text-primary);
            line-height: 1.6;
        }
        #app {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
        }
        nav ul {
            display: flex;
            list-style: none;
            gap: 20px;
        }
        nav a {
            color: var(--text-primary);
            text-decoration: none;
        }
        .music-player {
            background-color: var(--secondary-color);
            padding: 20px;
            border-radius: 10px;
            margin-bottom: 30px;
        }
        .track-info {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
        }
        .track-info img {
            width: 100px;
            height: 100px;
            margin-right: 20px;
            object-fit: cover;
        }
        .player-controls {
            display: flex;
            justify-content: center;
            gap: 20px;
            margin-bottom: 20px;
        }
        .player-controls button {
            background: none;
            border: none;
            font-size: 24px;
            cursor: pointer;
        }
        .progress-bar {
            width: 100%;
            height: 5px;
            background-color: #555;
            border-radius: 3px;
        }
        #progress {
            width: 0;
            height: 100%;
            background-color: var(--accent-color);
            border-radius: 3px;
        }
        .vote-container {
            display: flex;
            justify-content: space-between;
            gap: 20px;
        }
        .vote-option {
            background-color: var(--secondary-color);
            padding: 15px;
            border-radius: 8px;
            text-align: center;
            flex: 1;
        }
        .vote-option img {
            max-width: 200px;
            margin-bottom: 10px;
        }
        .vote-btn {
            background-color: var(--accent-color);
            color: var(--bg-primary);
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
        }
        footer {
            text-align: center;
            margin-top: 30px;
            padding: 20px;
            background-color: var(--secondary-color);
        }
        @media (max-width: 768px) {
            .vote-container {
                flex-direction: column;
            }
        }
    </style>
</head>
<body>
    <div id="app">
        <header>
            <div class="logo">SoundVote</div>
            <nav>
                <ul>
                    <li><a href="#home">Início</a></li>
                    <li><a href="#player">Player</a></li>
                    <li><a href="#vote">Votar</a></li>
                </ul>
            </nav>
        </header>

        <main>
            <section id="player">
                <div class="music-player">
                    <div class="track-info">
                        <img id="track-cover" src="https://via.placeholder.com/100" alt="Capa da Música">
                        <div class="track-details">
                            <h2 id="track-title">Título da Música</h2>
                            <p id="track-artist">Artista</p>
                        </div>
                    </div>
                    <div class="player-controls">
                        <button id="prev-btn">⏮️</button>
                        <button id="play-pause-btn">▶️</button>
                        <button id="next-btn">⏭️</button>
                    </div>
                    <div class="progress-bar">
                        <div id="progress"></div>
                    </div>
                </div>
            </section>

            <section id="vote">
                <h2>Vote na Próxima Música</h2>
                <div class="vote-container">
                    <div class="vote-option">
                        <img src="https://via.placeholder.com/200" alt="Música 1">
                        <h3>Música 1</h3>
                        <button class="vote-btn" onclick="voteSystem.vote('musica1')">Votar</button>
                    </div>
                    <div class="vote-option">
                        <img src="https://via.placeholder.com/200" alt="Música 2">
                        <h3>Música 2</h3>
                        <button class="vote-btn" onclick="voteSystem.vote('musica2')">Votar</button>
                    </div>
                </div>
            </section>
        </main>

        <footer>
            <p>© 2025 SoundVote. Todos os direitos reservados.</p>
        </footer>
    </div>

    <script>
        class MusicPlayer {
            constructor() {
                this.currentTrack = null;
                this.isPlaying = false;
                this.initializeControls();
            }

            initializeControls() {
                const playPauseBtn = document.getElementById('play-pause-btn');
                playPauseBtn.addEventListener('click', () => this.togglePlayPause());
            }

            togglePlayPause() {
                this.isPlaying = !this.isPlaying;
                const playPauseBtn = document.getElementById('play-pause-btn');
                playPauseBtn.textContent = this.isPlaying ? '⏸️' : '▶️';
            }
        }

        class VoteSystem {
            constructor() {
                this.votes = {};
            }

            vote(trackId) {
                this.votes[trackId] = (this.votes[trackId] || 0) + 1;
                this.updateVoteDisplay();
            }

            updateVoteDisplay() {
                console.log('Votos atuais:', this.votes);
            }

            getResults() {
                return this.votes;
            }
        }

        const player = new MusicPlayer();
        const voteSystem = new VoteSystem();

        // Simulação de atualização de música
        function updateTrackInfo() {
            const tracks = [
                { title: 'Música Exemplo 1', artist: 'Artista A', cover: 'https://via.placeholder.com/100' },
                { title: 'Música Exemplo 2', artist: 'Artista B', cover: 'https://via.placeholder.com/100' }
            ];

            const randomTrack = tracks[Math.floor(Math.random() * tracks.length)];
            
            document.getElementById('track-title').textContent = randomTrack.title;
            document.getElementById('track-artist').textContent = randomTrack.artist;
            document.getElementById('track-cover').src = randomTrack.cover;
        }

        // Inicialização
        document.addEventListener('DOMContentLoaded', () => {
            updateTrackInfo();
        });
    </script>
</body>
</html>
