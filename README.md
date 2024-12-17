<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Site de Jogos</title>
    <style>
        body {
            margin: 0;
            font-family: 'Arial', sans-serif;
            display: flex;
            flex-direction: column;
            min-height: 100vh; /* Garantir que o corpo ocupe toda a altura da tela */
            background-color: #1c1c1c; /* Fundo escuro, típico de sites de jogos */
            color: #fff;
        }

        /* Estilos para o navegador superior */
        .top-nav {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 50px;
            background-color: #222;
            color: white;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 0 15px;
            z-index: 1000;
        }

        .top-nav button {
            background: linear-gradient(to bottom, #f0f0f0, #d9d9d9);
            border: 1px solid #999;
            border-radius: 5px;
            color: #333;
            font-size: 16px;
            cursor: pointer;
            margin: 0 5px;
            padding: 5px 10px;
            box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.2);
            transition: all 0.2s ease;
        }

        .top-nav button:hover {
            background: linear-gradient(to bottom, #e0e0e0, #c0c0c0);
            box-shadow: 3px 3px 6px rgba(0, 0, 0, 0.3);
        }

        .top-nav button:active {
            box-shadow: inset 2px 2px 4px rgba(0, 0, 0, 0.3);
        }

        /* Estilos para o menu lateral transformado em menu horizontal */
        .side-nav {
            position: relative;
            top: 50px; /* Logo abaixo da barra superior */
            width: 100%;
            height: auto;
            background-color: #444;
            color: white;
            display: flex;
            justify-content: space-evenly;
            padding: 10px 0;
            box-sizing: border-box;
        }

        .side-nav button {
            background: linear-gradient(to bottom, #f0f0f0, #d9d9d9);
            border: 1px solid #999;
            border-radius: 5px;
            color: #333;
            font-size: 16px;
            cursor: pointer;
            padding: 10px 15px;
            box-shadow: 2px 2px 5px rgba(0, 0, 0, 0.2);
            transition: all 0.2s ease;
        }

        .side-nav button:hover {
            background: linear-gradient(to bottom, #e0e0e0, #c0c0c0);
            box-shadow: 3px 3px 6px rgba(0, 0, 0, 0.3);
        }

        .side-nav button:active {
            box-shadow: inset 2px 2px 4px rgba(0, 0, 0, 0.3);
        }

        /* Estilos para o conteúdo principal */
        .content {
            flex-grow: 1; /* Faz com que o conteúdo ocupe o espaço restante */
            padding: 20px;
            background-color: #111;
            box-sizing: border-box;
            display: none; /* Inicia como invisível até o "carregamento" ser concluído */
        }

        h2 {
            font-size: 28px;
            color: #FF5C5C; /* Cor vibrante, ideal para tema de jogos */
            margin-bottom: 20px;
        }

        article {
            background-color: #222;
            border-radius: 10px;
            padding: 20px;
        }

        section {
            margin-bottom: 20px;
        }

        section h3 {
            font-size: 24px;
            color: #F5C542; /* Cor dourada para os títulos das seções */
        }

        section p {
            font-size: 18px;
        }

        /* Estilos para o loader */
        .loader {
            width: 48px;
            height: 48px;
            border-radius: 50%;
            position: relative;
            animation: rotate 1s linear infinite;
        }

        .loader::before,
        .loader::after {
            content: "";
            box-sizing: border-box;
            position: absolute;
            inset: 0px;
            border-radius: 50%;
            border: 5px solid #FFF;
            animation: prixClipFix 2s linear infinite;
        }

        .loader::after {
            border-color: #FF3D00;
            animation: prixClipFix 2s linear infinite, rotate 0.5s linear infinite reverse;
            inset: 6px;
        }

        @keyframes rotate {
            0% {
                transform: rotate(0deg);
            }
            100% {
                transform: rotate(360deg);
            }
        }

        @keyframes prixClipFix {
            0% {
                clip-path: polygon(50% 50%, 0 0, 0 0, 0 0, 0 0, 0 0);
            }
            25% {
                clip-path: polygon(50% 50%, 0 0, 100% 0, 100% 0, 100% 0, 100% 0);
            }
            50% {
                clip-path: polygon(50% 50%, 0 0, 100% 0, 100% 100%, 100% 100%, 100% 100%);
            }
            75% {
                clip-path: polygon(50% 50%, 0 0, 100% 0, 100% 100%, 0 100%, 0 100%);
            }
            100% {
                clip-path: polygon(50% 50%, 0 0, 100% 0, 100% 100%, 0 100%, 0 0);
            }
        }

        @media (max-width: 768px) {
            .side-nav {
                flex-direction: column;
                align-items: center;
            }

            .content {
                margin-top: 120px;
            }
        }
    </style>
    <script>
        function toggleDropdown() {
            const dropdown = document.querySelector('.dropdown');
            dropdown.style.display = dropdown.style.display === 'flex' ? 'none' : 'flex';
        }

        window.onload = function() {
            // Simula o carregamento de conteúdo
            setTimeout(function() {
                document.querySelector('.loader').style.display = 'none';
                document.querySelector('.content').style.display = 'block';
            }, 3000); // Tempo de carregamento de 3 segundos
        };
    </script>
</head>
<body>

    <div class="top-nav">
        <button onclick="alert('Botão 1 clicado!')">Início</button>
        <button onclick="toggleDropdown()">Jogos</button>
        <button onclick="alert('Botão 3 clicado!')">Contatos</button>
    </div>

    <div class="side-nav">
        <button>PC</button>
        <button>Console</button>
        <button>Mobile</button>
        <button>Ação</button>
        <button>Estratégia</button>
    </div>

    <!-- Componente de carregamento -->
    <div class="loader"></div>

    <!-- Conteúdo principal -->
    <div class="content">
        <h2>Bem-vindo ao mundo dos jogos!</h2>
        <article>
            <section>
                <h3>Top Jogos de Ação</h3>
                <p>Explore os jogos de ação mais emocionantes, com gráficos incríveis e jogabilidade eletrizante. Prepare-se para desafios e muita diversão!</p>
            </section>
            <section>
                <h3>Jogos de Estratégia</h3>
                <p>Testes de estratégia que vão desafiar sua mente. Planeje suas jogadas, tome decisões difíceis e domine o campo de batalha.</p>
            </section>
        </article>
    </div>

</body>
</html>
