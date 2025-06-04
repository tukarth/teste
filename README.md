<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Portfólio Interativo</title>
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
        }

        header {
            padding: 20px;
            text-align: center;
            background-color: rgba(255, 255, 255, 0.05);
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.3);
        }

        header h1 {
            font-size: 2.5rem;
            animation: slideIn 1s ease-out;
        }

        nav {
            margin-top: 10px;
        }

        nav a {
            color: #1abc9c;
            margin: 0 15px;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
        }

        nav a:hover {
            color: #16a085;
        }

        section {
            max-width: 900px;
            margin: 40px auto;
            padding: 20px;
            background-color: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            backdrop-filter: blur(10px);
            animation: fadeIn 2s ease-in;
        }

        section h2 {
            font-size: 1.8rem;
            margin-bottom: 10px;
        }

        section p {
            font-size: 1rem;
            margin-bottom: 20px;
        }

        .project {
            margin-bottom: 20px;
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            overflow: hidden;
            transition: transform 0.3s;
        }

        .project:hover {
            transform: scale(1.02);
        }

        .project img {
            width: 100%;
            height: auto;
        }

        .project-description {
            padding: 10px;
        }

        .buttons {
            display: flex;
            flex-direction: column;
            gap: 15px;
            margin-top: 20px;
        }

        .buttons a {
            text-decoration: none;
            color: #fff;
            background: #1abc9c;
            padding: 10px 15px;
            font-size: 13px;
            text-align: center;
            border-radius: 10px;
            transition: background 0.3s ease;
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

        @keyframes slideIn {
            from { transform: translateY(-100px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        @keyframes fadeIn {
            from { opacity: 0; }
            to { opacity: 1; }
        }

        /* Estilos da galeria */
        .slideshow {
            position: relative;
            max-width: 600px;
            margin: auto;
        }

        .slideshow img {
            width: 100%;
            border-radius: 10px;
            display: none;
        }

        .slideshow img.active {
            display: block;
        }

        .carousel-button {
            margin: 10px 5px;
            padding: 10px 20px;
            font-size: 14px;
            border: none;
            border-radius: 8px;
            background-color: #1abc9c;
            color: #fff;
            cursor: pointer;
            transition: background 0.3s ease;
        }

        .carousel-button:hover {
            background-color: #16a085;
        }

        /* Estilos do formulário de blog */
        .blog-form {
            background-color: rgba(255, 255, 255, 0.1);
            border-radius: 10px;
            padding: 20px;
            margin-top: 20px;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.5);
        }

        .blog-form input,
        .blog-form textarea {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: none;
            border-radius: 5px;
        }

        .blog-form button {
            background-color: #007BFF;
            color: white;
            border: none;
            padding: 10px;
            cursor: pointer;
            border-radius: 5px;
            transition: background 0.3s;
        }

        .blog-form button:hover {
            background-color: #0056b3;
        }

        /* Responsividade */
        @media (max-width: 600px) {
            header h1 {
                font-size: 2rem;
            }

            nav a {
                margin: 0 10px;
            }

            section {
                padding: 15px;
            }
        }
    </style>
</head>
<body>

<header>
    <h1>Meu Portfólio Interativo</h1>
    <nav>
        <a href="#projetos">Projetos</a>
        <a href="#galeria">Galeria</a>
        <a href="#blog">Blog</a>
    </nav>
</header>

<section id="projetos">
    <h2>Projetos em Destaque</h2>
    <div class="project">
        <img src="https://via.placeholder.com/600x400" alt="Projeto 1">
        <div class="project-description">
            <h3>Projeto 1</h3>
            <p>Descrição do projeto 1. Este projeto envolve a criação de uma aplicação web para gerenciar tarefas.</p>
            <a href="#" class="buttons">Ver Detalhes</a>
        </div>
    </div>
    <div class="project">
        <img src="https://via.placeholder.com/600x400" alt="Projeto 2">
        <div class="project-description">
            <h3>Projeto 2</h3>
            <p>Descrição do projeto 2. Este projeto é um sistema de gerenciamento de biblioteca.</p>
            <a href="#" class="buttons">Ver Detalhes</a>
        </div>
    </div>
    <div class="project">
        <img src="https://via.placeholder.com/600x400" alt="Projeto 3">
        <div class="project-description">
            <h3>Projeto 3</h3>
            <p>Descrição do projeto 3. Um aplicativo móvel para rastreamento de hábitos.</p>
            <a href="#" class="buttons">Ver Detalhes</a>
        </div>
    </div>
</section>

<section id="galeria" style="text-align:center; margin-top:50px;">
    <h2>Galeria</h2>
    <div class="slideshow">
        <img src="https://via.placeholder.com/600x400" alt="Foto 1" class="slide active">
        <img src="https://via.placeholder.com/600x400" alt="Foto 2" class="slide">
        <img src="https://via.placeholder.com/600x400" alt="Foto 3" class="slide">
        <img src="https://via.placeholder.com/600x400" alt="Foto 4" class="slide">
        <button class="carousel-button" onclick="mudarSlide(-1)">❮ Anterior</button>
        <button class="carousel-button" onclick="mudarSlide(1)">Próximo ❯</button>
    </div>
</section>

<section id="blog" class="blog-form">
    <h2>Atualizações do Blog</h2>
    <form id="formBlog" onsubmit="adicionarPost(event)">
        <input type="text" id="titulo" placeholder="Título do Post" required>
        <textarea id="conteudo" placeholder="Conteúdo do Post" rows="4" required></textarea>
        <button type="submit">Adicionar Post</button>
    </form>
    <div id="posts" style="margin-top: 20px;"></div>
</section>

<footer>
    @tukarth - Todos os direitos reservados. &copy; 2025
</footer>

<script>
    let slides = document.querySelectorAll(".slide");
    let index = 0;

    function showSlide() {
        slides.forEach((slide, i) => {
            slide.classList.remove("active");
            if (i === index) {
                slide.classList.add("active");
            }
        });
    }

    function mudarSlide(step) {
        index = (index + step + slides.length) % slides.length;
        showSlide();
    }

    function autoSlide() {
        index = (index + 1) % slides.length;
        showSlide();
    }

    setInterval(autoSlide, 3000); // Troca automática a cada 3 segundos
    showSlide(); // Exibe a primeira imagem

    // Função para adicionar post ao blog
    function adicionarPost(event) {
        event.preventDefault();
        const titulo = document.getElementById('titulo').value;
        const conteudo = document.getElementById('conteudo').value;

        const postDiv = document.createElement('div');
        postDiv.style.marginTop = '20px';
        postDiv.style.padding = '10px';
        postDiv.style.border = '1px solid rgba(255, 255, 255, 0.1)';
        postDiv.style.borderRadius = '10px';
        postDiv.style.backgroundColor = 'rgba(255, 255, 255, 0.05)';

        postDiv.innerHTML = `<h3>${titulo}</h3><p>${conteudo}</p>`;
        document.getElementById('posts').prepend(postDiv);

        // Limpa o formulário
        document.getElementById('formBlog').reset();
    }
</script>
</body>
</html>
