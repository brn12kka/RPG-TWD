<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Federação Interestadual de Ruas Unidas - Estatísticas</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: #f4f4f4;
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        h1 {
            color: #333;
            text-align: center;
        }
        .search-container {
            margin-bottom: 20px;
            width: 100%;
            max-width: 600px;
        }
        #searchInput {
            width: 100%;
            padding: 10px;
            font-size: 16px;
            border: 2px solid #ccc;
            border-radius: 5px;
            box-sizing: border-box;
        }
        #playerList {
            width: 100%;
            max-width: 600px;
            margin-bottom: 20px;
        }
        .player-item {
            background-color: #fff;
            padding: 15px;
            margin: 10px 0;
            border-radius: 5px;
            cursor: pointer;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            transition: transform 0.2s;
        }
        .player-item:hover {
            transform: scale(1.02);
        }
        #playerDetails {
            width: 100%;
            max-width: 600px;
            background-color: #fff;
            padding: 20px;
            border-radius: 5px;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
            display: none;
        }
        #playerDetails h2 {
            margin-top: 0;
            color: #2c3e50;
        }
        #playerDetails p {
            margin: 5px 0;
        }
        .stat-label {
            font-weight: bold;
            color: #2980b9;
        }
        @media (max-width: 600px) {
            body {
                padding: 10px;
            }
            .player-item, #playerDetails {
                padding: 10px;
            }
        }
    </style>
</head>
<body>
    <h1>Federação Interestadual de Ruas Unidas</h1>
    <div class="search-container">
        <input type="text" id="searchInput" placeholder="Pesquisar jogador...">
    </div>
    <div id="playerList"></div>
    <div id="playerDetails"></div>

    <script>
        // Dados fictícios dos jogadores (substitua com os dados reais)
        const players = [
            {
                name: "Lucas",
                goals: 5,
                assists: 1,
                titles: ["1x Copa das Estrelas"],
                awards: ["1x Bola de Ouro"]
            },
            {
                name: "Breno",
                goals: 2,
                assists: 2,
                titles: ["1x Copa das Estrelas"],
                awards: ["1x Bola de Ouro, 2x Artilheiro, 1x Melhor Defensor, 2x Lider de Assistências, 1x Puskas"]
            },
            {
                name: "Vitor Gordo",
                goals: 1,
                assists: 3,
                titles: [],
                awards: []
            },
            {
                name: "Michel",
                goals: 3,
                assists: 2,
                titles: [],
                awards: []
            },
            {
                name: "Biel",
                goals: 0,
                assists: 0,
                titles: [],
                awards: ["1x Premio Revelação"],
            },
            {
                name: "Otávio",
                goals: 0,
                assists: 0,
                titles: [],
                awards: [],
            },
            {
                name: "Vitinho",
                goals: 0,
                assists: 0,
                titles: [],
                awards: [],
            },
             {
                name: "Vitor Magro",
                goals: 0,
                assists: 0,
                titles: [],
                awards: [],
            },
        ];

        // Elementos DOM
        const searchInput = document.getElementById('searchInput');
        const playerList = document.getElementById('playerList');
        const playerDetails = document.getElementById('playerDetails');

        // Função para exibir a lista de jogadores
        function displayPlayers(playersToShow) {
            playerList.innerHTML = '';
            playersToShow.forEach(player => {
                const playerDiv = document.createElement('div');
                playerDiv.classList.add('player-item');
                playerDiv.textContent = player.name;
                playerDiv.addEventListener('click', () => showPlayerDetails(player));
                playerList.appendChild(playerDiv);
            });
        }

        // Função para exibir detalhes do jogador
        function showPlayerDetails(player) {
            playerDetails.style.display = 'block';
            playerDetails.innerHTML = `
                <h2>${player.name}</h2>
                <p><span class="stat-label">Gols:</span> ${player.goals}</p>
                <p><span class="stat-label">Assistências:</span> ${player.assists}</p>
                <p><span class="stat-label">Títulos Coletivos:</span> ${player.titles.length > 0 ? player.titles.join(', ') : 'Nenhum'}</p>
                <p><span class="stat-label">Prêmios Individuais:</span> ${player.awards.length > 0 ? player.awards.join(', ') : 'Nenhum'}</p>
            `;
        }

        // Função de busca
        searchInput.addEventListener('input', () => {
            const searchTerm = searchInput.value.toLowerCase();
            const filteredPlayers = players.filter(player => 
                player.name.toLowerCase().includes(searchTerm)
            );
            displayPlayers(filteredPlayers);
        });

        // Exibir todos os jogadores inicialmente
        displayPlayers(players);
    </script>
</body>
</html>
