<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Entre no Projeto</title>
  <style>
    body {
      font-family: 'Inter', sans-serif;
      line-height: 1.6;
      margin: 0;
      padding: 0;
      display: flex;
      min-height: 100vh;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      background-color: #233237;
      color: #E0E0E0;
    }

    .container {
      width: 100%;
      max-width: 420px;
      padding: 24px;
    }

    .card {
      background-color: #2A3B40;
      border-radius: 0.5rem;
      box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
      border: 1px solid #3E5055;
    }

    .card-header {
      text-align: center;
      padding: 24px;
    }

    .logo-container {
      margin: 0 auto 1rem;
      display: flex;
      height: 4rem;
      width: 4rem;
      align-items: center;
      justify-content: center;
      border-radius: 9999px;
      background-color: #74EBD5;
      color: #233237;
    }

    .logo-container svg {
      width: 32px;
      height: 32px;
    }

    .card-title {
      font-size: 1.875rem;
      font-weight: 700;
      color: #E0E0E0;
    }

    .card-description {
      color: #A0AEC0;
      font-size: 0.875rem;
    }

    .card-content {
      padding: 0 24px 24px 24px;
    }

    .form-group {
      margin-bottom: 1.5rem;
    }

    .form-group label {
      display: block;
      margin-bottom: 0.5rem;
      font-size: 0.875rem;
      font-weight: 500;
      color: #E0E0E0;
    }

    .form-group input {
      width: 100%;
      padding: 0.75rem 1rem;
      border: 1px solid #3E5055;
      border-radius: 0.375rem;
      background-color: #2A3B40;
      color: #E0E0E0;
      font-size: 1rem;
    }

    .form-group input:focus {
      outline: none;
      border-color: #74EBD5;
      box-shadow: 0 0 0 2px rgba(116, 235, 213, 0.5);
    }

    .submit-button {
      width: 100%;
      padding: 0.75rem 1rem;
      background-color: #74EBD5;
      color: #233237;
      border: none;
      border-radius: 0.375rem;
      font-size: 0.875rem;
      font-weight: 500;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 0.5rem;
    }

    .submit-button:hover {
      background-color: #5cb8a9;
    }

    .submit-button svg {
      width: 20px;
      height: 20px;
    }

    .card-footer {
      margin-top: 1rem;
      padding: 0 24px 24px 24px;
      text-align: center;
      font-size: 0.875rem;
    }

    .card-footer p {
      color: #A0AEC0;
      margin: 0;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="card">
      <div class="card-header">
        <div class="logo-container">
          <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" stroke="currentColor" stroke-width="2"
            stroke-linecap="round" stroke-linejoin="round">
            <path d="M10 18a2 2 0 1 1-4 0 2 2 0 0 1 4 0Z" />
            <path d="M20 6a2 2 0 1 1-4 0 2 2 0 0 1 4 0Z" />
            <path d="m4.5 16.5 7.5-9" />
            <path d="m12 15 7.5-9" />
          </svg>
        </div>
        <h1 class="card-title">Entre no Projeto</h1>
        <p class="card-description">Acesse para explorar os projetos</p>
      </div>
      <div class="card-content">
        <form action="http://localhost:3000/goto/PzrYhNLNR?orgId=1" method="GET">
          <div class="form-group">
            <label for="username">Usuário</label>
            <input id="username" type="text" placeholder="Seu usuário" required>
          </div>
          <div class="form-group">
            <label for="password">Senha</label>
            <input id="password" type="password" placeholder="Sua senha" required>
          </div>
          <button type="submit" class="submit-button">
            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" fill="none" stroke="currentColor" stroke-width="2"
              stroke-linecap="round" stroke-linejoin="round">
              <path d="M15 3h4a2 2 0 0 1 2 2v14a2 2 0 0 1-2 2h-4" />
              <polyline points="10 17 15 12 10 7" />
              <line x1="15" x2="3" y1="12" y2="12" />
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
