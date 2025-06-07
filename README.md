<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Entre no Projeto</title>
  <style>
    body {
      font-family: 'Inter', sans-serif;
      background-color: #1e2a2f;
      color: #e0e0e0;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
    }

    .container {
      width: 100%;
      max-width: 400px;
      padding: 20px;
    }

    .card {
      background-color: #2a3b40;
      border-radius: 12px;
      box-shadow: 0 8px 24px rgba(0, 0, 0, 0.2);
      padding: 24px;
    }

    .card-header {
      text-align: center;
      margin-bottom: 24px;
    }

    .logo-container {
      width: 64px;
      height: 64px;
      background: #74EBD5;
      border-radius: 50%;
      display: flex;
      align-items: center;
      justify-content: center;
      margin: 0 auto 16px;
      color: #1e2a2f;
    }

    .logo-container svg {
      width: 28px;
      height: 28px;
    }

    .card-title {
      font-size: 1.8rem;
      font-weight: bold;
      margin-bottom: 8px;
    }

    .card-description {
      font-size: 0.9rem;
      color: #a0aec0;
    }

    .form-group {
      margin-bottom: 20px;
    }

    .form-group label {
      font-size: 0.85rem;
      margin-bottom: 6px;
      display: block;
    }

    .form-group input {
      width: 100%;
      padding: 10px;
      border-radius: 6px;
      border: 1px solid #3e5055;
      background-color: #2a3b40;
      color: #e0e0e0;
      font-size: 1rem;
    }

    .form-group input:focus {
      outline: none;
      border-color: #74EBD5;
      box-shadow: 0 0 0 2px rgba(116, 235, 213, 0.5);
    }

    .submit-button {
      width: 100%;
      padding: 12px;
      background-color: #74EBD5;
      color: #1e2a2f;
      font-weight: 600;
      border: none;
      border-radius: 6px;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      transition: background 0.3s ease;
    }

    .submit-button:hover {
      background-color: #5cb8a9;
    }

    .submit-button svg {
      width: 20px;
      height: 20px;
    }

    .card-footer {
      text-align: center;
      font-size: 0.8rem;
      color: #a0aec0;
      margin-top: 16px;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="card">
      <div class="card-header">
        <div class="logo-container">
          <svg xmlns="http://localhost:3000/goto/ut61hNYHR?orgId=1" fill="none" stroke="currentColor" stroke-width="2"
            stroke-linecap="round" stroke-linejoin="round" viewBox="0 0 24 24">
            <path d="M10 18a2 2 0 1 1-4 0 2 2 0 0 1 4 0Z"/>
            <path d="M20 6a2 2 0 1 1-4 0 2 2 0 0 1 4 0Z"/>
            <path d="m4.5 16.5 7.5-9"/>
            <path d="m12 15 7.5-9"/>
          </svg>
        </div>
        <h1 class="card-title">Entre no Projeto</h1>
        <p class="card-description">Acesse para explorar os projetos compartilhados.</p>
      </div>

      <div class="card-content">
        <form>
          <div class="form-group">
            <label for="username">Usuário</label>
            <input id="username" name="username" type="text" placeholder="Seu usuário">
          </div>
          <div class="form-group">
            <label for="password">Senha</label>
            <input id="password" name="password" type="password" placeholder="Sua senha">
          </div>
          <button type="submit" class="submit-button">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" stroke="currentColor"
              stroke-width="2" stroke-linecap="round" stroke-linejoin="round" viewBox="0 0 24 24">
              <path d="M15 3h4a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2h-4"/>
              <polyline points="10 17 15 12 10 7"/>
              <line x1="15" x2="3" y1="12" y2="12"/>
            </svg>
            Entrar
          </button>
        </form>
      </div>

      <div class="card-footer">
        <p>Este é um formulário de demonstração.</p>
      </div>
    </div>
  </div>
</body>
</html>
