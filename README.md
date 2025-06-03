<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Projetos Acadêmicos</title>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;500;700&display=swap" rel="stylesheet">
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Poppins', sans-serif;
    }

    body {
      background-color: #000;
      color: #fff;
      line-height: 1.6;
      overflow-x: hidden;
      transition: background 0.5s, color 0.5s;
    }

    .dark-mode {
      background-color: #222;
      color: #fff;
    }

    header {
      padding: 30px;
      text-align: center;
      background-color: rgba(255, 255, 255, 0.05);
      box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
    }

    section {
      max-width: 900px;
      margin: 40px auto;
      padding: 20px;
      background-color: rgba(255, 255, 255, 0.05);
      border-radius: 15px;
      backdrop-filter: blur(10px);
    }

    .buttons a {
      text-decoration: none;
      color: #fff;
      background: #1abc9c;
      padding: 10px 15px;
      font-size: 14px;
      text-align: center;
      border-radius: 10px;
      display: block;
      width: max-content;
      margin: 10px auto;
    }

    .buttons a:hover {
      background: #16a085;
    }

    footer {
      text-align: center;
      margin-top: 50px;
      padding: 20px;
      font-size: 0.9rem;
      color: #aaa;
    }

    /* Estilos da galeria */
    .carousel img {
      width: 100%;
      max-width: 600px;
      height: auto;
      border-radius: 10px;
    }

    /* Botão de alternar tema */
    .theme-toggle {
      display: flex;
      justify-content: center;
      margin-top: 20px;
    }

    .theme-toggle button {
      background: #007BFF;
      color: white;
      border: none;
      padding: 10px;
      cursor: pointer;
      border-radius: 8px;
      font-size: 14px;
    }

    .search-bar {
      text-align: center;
      margin: 20px 0;
    }

    .search-bar input {
      padding: 10px;
      font-size: 16px;
      width: 80%;
      max-width: 600px;
      border-radius: 8px;
      border: none;
    }

    .comments-section {
      text-align: center;
      margin: 40px auto;
    }

    .comments-section textarea {
      width: 80%;
      max-width: 600px;
      padding: 10px;
      border-radius: 8px;
    }

    .comments-section button {
      padding: 10px;
      background: #007BFF;
      color: white;
      border: none;
      cursor: pointer;
      border-radius: 8px;
    }

  </style>
</head>
<body>

  <header>
    <h1>Projetos Acadêmicos</h1>
  </header>

  <div class="theme-toggle">
    <button onclick="toggleTheme()">Alternar Tema</button>
  </div>

  <section>
    <h2>Projetos em Destaque</h2>
    <p>Confira projetos acadêmicos organizados de forma visual e intuitiva.</p>
    <div class="buttons">
      <a href="https://drive.google.com/drive/folders/1bJ27rtxhDxfna8sEtnO4MQNsp3kygkso?usp=sharing">🔗 Acesso Projetos</a>
      <a href="SECURITY.md">Security Policy</a>
    </div>
  </section>

  <div class="search-bar">
    <input type="text" id="searchBar" placeholder="Pesquisar projetos..." onkeyup="searchProjects()">
    <ul id="projectList">
      <li>Projeto 1</li>
      <li>Projeto 2</li>
      <li>Projeto 3</li>
    </ul>
  </div>

  <section class="comments-section">
    <h3>Deixe seu comentário</h3>
    <textarea id="commentBox" placeholder="Escreva algo..." rows="4"></textarea>
    <button onclick="addComment()">Enviar</button>
    <ul id="commentList"></ul>
  </section>

  <footer>
    @tukarth - Todos os direitos reservados. &copy; 2025
  </footer>

  <script>
    function toggleTheme() {
      document.body.classList.toggle("dark-mode");
    }

    function searchProjects() {
      let input = document.getElementById("searchBar").value.toLowerCase();
      let projects = document.querySelectorAll("#projectList li");

      projects.forEach(project => {
        project.style.display = project.textContent.toLowerCase().includes(input) ? "block" : "none";
      });
    }

    function addComment() {
      let commentBox = document.getElementById("commentBox");
      if (commentBox.value.trim() !== "") {
        let comment = document.createElement("li");
        comment.textContent = commentBox.value;
        document.getElementById("commentList").appendChild(comment);
        commentBox.value = "";
      }
    }
  </script>

</body>
</html>
