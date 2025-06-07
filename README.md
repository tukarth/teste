
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vitrine de Código - Login</title>
    <style>
        body {
            font-family: 'Inter', -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji";
            line-height: 1.6;
            margin: 0;
            padding: 0;
            display: flex;
            min-height: 100vh;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            background-color: #233237; /* Cor de fundo similar ao tema escuro */
            color: #E0E0E0; /* Cor de texto clara */
        }
        .container {
            width: 100%;
            max-width: 420px; /* max-w-md */
            padding: 24px; /* p-6 */
        }
        .card {
            background-color: #2A3B40; /* Cor de card um pouco mais clara que o fundo */
            border-radius: 0.5rem; /* rounded-lg */
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05); /* shadow-2xl */
            border: 1px solid #3E5055; /* Cor da borda sutil */
        }
        .card-header {
            text-align: center;
            padding: 24px; /* p-6 */
        }
        .logo-container {
            margin-left: auto;
            margin-right: auto;
            margin-bottom: 1rem; /* mb-4 */
            display: flex;
            height: 4rem; /* h-16 */
            width: 4rem; /* w-16 */
            align-items: center;
            justify-content: center;
            border-radius: 9999px; /* rounded-full */
            background-color: #74EBD5; /* bg-primary */
            color: #233237; /* text-primary-foreground */
        }
        .logo-container svg {
            width: 32px;
            height: 32px;
        }
        .card-title {
            font-size: 1.875rem; /* text-3xl */
            font-weight: 700; /* font-headline (aproximado) */
            color: #E0E0E0;
        }
        .card-description {
            color: #A0AEC0; /* text-muted-foreground (aproximado) */
            font-size: 0.875rem; /* text-sm */
        }
        .card-content {
            padding: 24px; /* p-6 */
            padding-top: 0;
        }
        .form-group {
            margin-bottom: 1.5rem; /* space-y-6 -> space-y-2 em cada div */
        }
        .form-group label {
            display: block;
            margin-bottom: 0.5rem; /* space-y-2 -> mb (aproximado) */
            font-size: 0.875rem; /* text-sm */
            font-weight: 500; /* font-medium */
            color: #E0E0E0;
        }
        .form-group input {
            width: calc(100% - 24px); /* w-full com padding */
            padding: 0.75rem 1rem; /* px-3 py-2 (ajustado para input h-10) */
            border: 1px solid #3E5055; /* border-input */
            border-radius: 0.375rem; /* rounded-md */
            background-color: #2A3B40; /* bg-card */
            color: #E0E0E0;
            font-size: 1rem; /* text-base */
        }
        .form-group input:focus {
            outline: none;
            border-color: #74EBD5; /* ring-primary (aproximado) */
            box-shadow: 0 0 0 2px rgba(116, 235, 213, 0.5); /* ring-offset-background e ring-ring */
        }
        .submit-button {
            width: 100%;
            padding: 0.75rem 1rem;
            background-color: #74EBD5; /* bg-primary */
            color: #233237; /* text-primary-foreground */
            border: none;
            border-radius: 0.375rem; /* rounded-md */
            font-size: 0.875rem; /* text-sm */
            font-weight: 500; /* font-medium */
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 0.5rem; /* mr-2 */
        }
        .submit-button:hover {
            background-color: #5cb8a9; /* hover:bg-primary/90 */
        }
        .submit-button svg {
            width: 20px; /* w-5 */
            height: 20px; /* h-5 */
        }
        .card-footer {
            margin-top: 1rem; /* mt-4 */
            padding: 24px; /* p-6 */
            padding-top: 0;
            text-align: center;
            font-size: 0.875rem; /* text-sm */
        }
        .card-footer p {
            color: #A0AEC0; /* text-muted-foreground */
            margin: 0;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="card">
            <div class="card-header">
                <div class="logo-container">
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                        <path d="M10 18a2 2 0 1 1-4 0 2 2 0 0 1 4 0Z"/>
                        <path d="M20 6a2 2 0 1 1-4 0 2 2 0 0 1 4 0Z"/>
                        <path d="m4.5 16.5 7.5-9"/>
                        <path d="m12 15 7.5-9"/>
                    </svg>
                </div>
                <h1 class="card-title">Vitrine de Código</h1>
                <p class="card-description">Acesse para explorar os projetos</p>
            </div>
            <div class="card-content">
                <form>
                    <div class="form-group">
                        <label for="username">Usuário</label>
                        <input id="username" type="text" placeholder="Seu usuário" value="" readonly>
                    </div>
                    <div class="form-group">
                        <label for="password">Senha</label>
                        <input id="password" type="password" placeholder="Sua senha" value="" readonly>
                    </div>
                    <button type="submit" class="submit-button">
                        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
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

    
