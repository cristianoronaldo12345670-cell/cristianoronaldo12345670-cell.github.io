<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ochuckydo - Esqueleto Humano</title>
    <link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>💀</text></svg>">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: linear-gradient(135deg, #1a5e1a 0%, #2d8f2d 50%, #1a5e1a 100%);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            min-height: 100vh;
            padding: 15px;
            display: flex;
            justify-content: center;
        }

        .container {
            max-width: 800px;
            width: 100%;
            text-align: center;
        }

        .header {
            background: rgba(255, 255, 255, 0.1);
            backdrop-filter: blur(10px);
            border-radius: 25px;
            padding: 25px;
            margin-bottom: 25px;
            border: 2px solid rgba(255, 255, 255, 0.2);
        }

        .logo-nome {
            color: #FFD700;
            font-size: 1.8rem;
            font-weight: bold;
            text-shadow: 2px 2px 8px rgba(0,0,0,0.5);
            margin-bottom: 5px;
            letter-spacing: 2px;
        }

        .titulo-principal {
            color: white;
            font-size: 2rem;
            font-weight: bold;
            text-shadow: 2px 2px 8px rgba(0,0,0,0.5);
            margin-bottom: 15px;
            letter-spacing: 1px;
        }

        .subtitulo {
            color: #e0e0e0;
            font-size: 1.1rem;
            margin-bottom: 20px;
        }

        .botao-info {
            background: linear-gradient(145deg, #ff3333, #cc0000);
            color: white;
            border: 3px solid #fff;
            padding: 18px 35px;
            font-size: 1.4rem;
            font-weight: bold;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 10px 25px rgba(0,0,0,0.4);
            letter-spacing: 1px;
            position: relative;
            overflow: hidden;
        }

        .botao-info:hover {
            background: linear-gradient(145deg, #ff4444, #dd0000);
            transform: translateY(-3px);
            box-shadow: 0 15px 35px rgba(0,0,0,0.5);
        }

        .botao-info:active {
            transform: translateY(0);
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
        }

        .esqueleto-container {
            display: none;
            background: linear-gradient(180deg, #f5f5f5 0%, #e0e0e0 100%);
            border-radius: 30px;
            padding: 30px 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.5);
            animation: aparecer 0.8s ease-out;
        }

        .esqueleto-container.visivel {
            display: block;
        }

        @keyframes aparecer {
            from {
                opacity: 0;
                transform: translateY(50px) scale(0.9);
            }
            to {
                opacity: 1;
                transform: translateY(0) scale(1);
            }
        }

        .esqueleto-visual {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 15px;
            padding: 20px;
        }

        .cabeca {
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 10px;
        }

        .cranio-emoji {
            font-size: 6rem;
            filter: drop-shadow(0 5px 10px rgba(0,0,0,0.3));
            animation: flutuar 3s ease-in-out infinite;
        }

        @keyframes flutuar {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }

        .osso-grupo {
            background: linear-gradient(145deg, #2d8f2d, #1a5e1a);
            color: white;
            border-radius: 20px;
            padding: 12px 25px;
            font-weight: bold;
            font-size: 1.3rem;
            margin: 10px 0;
            width: 100%;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
            text-align: center;
            letter-spacing: 1px;
        }

        .osso-item {
            background: white;
            border: 2px solid #2d8f2d;
            border-radius: 15px;
            padding: 12px 20px;
            margin: 8px 0;
            width: 100%;
            display: flex;
            align-items: center;
            box-shadow: 0 3px 10px rgba(0,0,0,0.2);
            transition: all 0.3s ease;
            position: relative;
        }

        .osso-item:hover {
            transform: translateX(10px);
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
            background: #f0f8f0;
        }

        .numero-osso {
            background: linear-gradient(145deg, #ff3333, #cc0000);
            color: white;
            border-radius: 50%;
            width: 35px;
            height: 35px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 1rem;
            margin-right: 15px;
            flex-shrink: 0;
            box-shadow: 0 2px 8px rgba(255,0,0,0.4);
        }

        .nome-osso {
            font-weight: bold;
            color: #333;
            font-size: 1.1rem;
        }

        .descricao-osso {
            color: #666;
            font-size: 0.9rem;
            margin-top: 3px;
        }

        .info-adicional {
            background: #ffd700;
            border-radius: 15px;
            padding: 15px;
            margin: 15px 0;
            font-weight: bold;
            color: #333;
            box-shadow: 0 5px 15px rgba(0,0,0,0.2);
        }

        .divisor {
            width: 5px;
            height: 30px;
            background: linear-gradient(180deg, #2d8f2d, #1a5e1a);
            margin: 10px auto;
            border-radius: 5px;
        }

        .linha-conexao {
            width: 3px;
            height: 25px;
            background: #2d8f2d;
            margin: 0 auto;
            position: relative;
        }

        .linha-conexao::after {
            content: '▼';
            position: absolute;
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
            color: #2d8f2d;
            font-size: 1rem;
        }

        .creditos {
            margin-top: 20px;
            padding: 15px;
            background: rgba(255, 255, 255, 0.9);
            border-radius: 15px;
            color: #333;
            font-weight: bold;
            font-size: 1rem;
        }

        .creditos span {
            color: #cc0000;
            font-size: 1.2rem;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <div class="logo-nome">☠️ OCHUCKYD O</div>
            <h1 class="titulo-principal">🦴 Sistema Esquelético Humano</h1>
            <p class="subtitulo">Guia Anatômico Completo - 206 Ossos</p>
            <button class="botao-info" onclick="mostrarEsqueleto()">
                🔍 Revelar Esqueleto
            </button>
        </div>

        <div id="esqueleto" class="esqueleto-container">
            <div class="esqueleto-visual">
                
                <!-- CABEÇA -->
                <div class="cabeca">
                    <div class="cranio-emoji">💀</div>
                    <div class="osso-grupo">🧠 CABEÇA E PESCOÇO</div>
                </div>

                <!-- Crânio -->
                <div class="osso-item">
                    <div class="numero-osso">1</div>
                    <div>
                        <div class="nome-osso">Osso Frontal</div>
                        <div class="descricao-osso">Testa e parte anterior do crânio</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">2</div>
                    <div>
                        <div class="nome-osso">Ossos Parietais (2)</div>
                        <div class="descricao-osso">Topo e laterais do crânio</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">3</div>
                    <div>
                        <div class="nome-osso">Ossos Temporais (2)</div>
                        <div class="descricao-osso">Laterais do crânio, contêm os ouvidos</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">4</div>
                    <div>
                        <div class="nome-osso">Osso Occipital</div>
                        <div class="descricao-osso">Parte posterior e base do crânio</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">5</div>
                    <div>
                        <div class="nome-osso">Ossos Zigomáticos (2)</div>
                        <div class="descricao-osso">Maçãs do rosto</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">6</div>
                    <div>
                        <div class="nome-osso">Maxila Superior</div>
                        <div class="descricao-osso">Osso superior da boca</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">7</div>
                    <div>
                        <div class="nome-osso">Mandíbula</div>
                        <div class="descricao-osso">Osso inferior da boca (queixo)</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">8</div>
                    <div>
                        <div class="nome-osso">Ossos Nasais (2)</div>
                        <div class="descricao-osso">Formam o nariz</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">9</div>
                    <div>
                        <div class="nome-osso">Osso Hioide</div>
                        <div class="descricao-osso">Sustenta a língua no pescoço</div>
                    </div>
                </div>

                <div class="linha-conexao"></div>

                <!-- TÓRAX -->
                <div class="osso-grupo">🫁 TÓRAX E COLUNA</div>

                <div class="osso-item">
                    <div class="numero-osso">10</div>
                    <div>
                        <div class="nome-osso">Clavículas (2)</div>
                        <div class="descricao-osso">Ligam os ombros ao esterno</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">11</div>
                    <div>
                        <div class="nome-osso">Escápulas (2)</div>
                        <div class="descricao-osso">Omoplatas, parte posterior dos ombros</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">12</div>
                    <div>
                        <div class="nome-osso">Esterno</div>
                        <div class="descricao-osso">Osso central do peito</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">13</div>
                    <div>
                        <div class="nome-osso">Costelas (24)</div>
                        <div class="descricao-osso">12 pares protegendo os órgãos</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">14</div>
                    <div>
                        <div class="nome-osso">Vértebras Cervicais (7)</div>
                        <div class="descricao-osso">Pescoço</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">15</div>
                    <div>
                        <div class="nome-osso">Vértebras Torácicas (12)</div>
                        <div class="descricao-osso">Parte superior das costas</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">16</div>
                    <div>
                        <div class="nome-osso">Vértebras Lombares (5)</div>
                        <div class="descricao-osso">Parte inferior das costas</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">17</div>
                    <div>
                        <div class="nome-osso">Sacro</div>
                        <div class="descricao-osso">Base da coluna vertebral</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">18</div>
                    <div>
                        <div class="nome-osso">Cóccix</div>
                        <div class="descricao-osso">Extremidade inferior da coluna</div>
                    </div>
                </div>

                <div class="linha-conexao"></div>

                <!-- MEMBROS SUPERIORES -->
                <div class="osso-grupo">💪 MEMBROS SUPERIORES (BRAÇOS)</div>

                <div class="osso-item">
                    <div class="numero-osso">19</div>
                    <div>
                        <div class="nome-osso">Úmeros (2)</div>
                        <div class="descricao-osso">Ossos dos braços</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">20</div>
                    <div>
                        <div class="nome-osso">Rádios (2)</div>
                        <div class="descricao-osso">Antebraço, lado do polegar</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">21</div>
                    <div>
                        <div class="nome-osso">Ulnas (2)</div>
                        <div class="descricao-osso">Antebraço, lado do mindinho</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">22</div>
                    <div>
                        <div class="nome-osso">Ossos Carpais (16)</div>
                        <div class="descricao-osso">Pulsos</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">23</div>
                    <div>
                        <div class="nome-osso">Ossos Metacarpais (10)</div>
                        <div class="descricao-osso">Palmas das mãos</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">24</div>
                    <div>
                        <div class="nome-osso">Falanges das Mãos (28)</div>
                        <div class="descricao-osso">Dedos das mãos</div>
                    </div>
                </div>

                <div class="linha-conexao"></div>

                <!-- MEMBROS INFERIORES -->
                <div class="osso-grupo">🦵 MEMBROS INFERIORES (PERNAS)</div>

                <div class="osso-item">
                    <div class="numero-osso">25</div>
                    <div>
                        <div class="nome-osso">Ossos do Quadril (2)</div>
                        <div class="descricao-osso">Pelve, une as pernas ao tronco</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">26</div>
                    <div>
                        <div class="nome-osso">Fêmures (2)</div>
                        <div class="descricao-osso">Ossos das coxas - maiores do corpo</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">27</div>
                    <div>
                        <div class="nome-osso">Patelas (2)</div>
                        <div class="descricao-osso">Rótulas dos joelhos</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">28</div>
                    <div>
                        <div class="nome-osso">Tíbias (2)</div>
                        <div class="descricao-osso">Ossos da canela</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">29</div>
                    <div>
                        <div class="nome-osso">Fíbulas (2)</div>
                        <div class="descricao-osso">Ossos laterais das pernas</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">30</div>
                    <div>
                        <div class="nome-osso">Ossos Tarsais (14)</div>
                        <div class="descricao-osso">Tornozelos e calcanhares</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">31</div>
                    <div>
                        <div class="nome-osso">Ossos Metatarsais (10)</div>
                        <div class="descricao-osso">Plantas dos pés</div>
                    </div>
                </div>

                <div class="osso-item">
                    <div class="numero-osso">32</div>
                    <div>
                        <div class="nome-osso">Falanges dos Pés (28)</div>
                        <div class="descricao-osso">Dedos dos pés</div>
                    </div>
                </div>

                <div class="info-adicional">
                    ✅ TOTAL: 206 OSSOS NO CORPO HUMANO ADULTO
                </div>

                <div class="creditos">
                    Criado por <span>☠️ OCHUCKYD O</span>
                </div>
            </div>
        </div>
    </div>

    <script>
        function mostrarEsqueleto() {
            const esqueleto = document.getElementById('esqueleto');
            esqueleto.classList.toggle('visivel');
            
            const botao = document.querySelector('.botao-info');
            if (esqueleto.classList.contains('visivel')) {
                botao.textContent = '🙈 Ocultar Esqueleto';
                setTimeout(() => {
                    esqueleto.scrollIntoView({ behavior: 'smooth', block: 'start' });
                }, 100);
            } else {
                botao.textContent = '🔍 Revelar Esqueleto';
            }
        }
    </script>
</body>
</html>
