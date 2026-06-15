# construindo-flashcards-<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Projeto: O Modelo de Caixa (Box Model)</title>
    <style>
        /* ==========================================================================
           1. O RESET (Aplicado apenas na seção da direita para fins de comparação)
           ========================================================================== */
        .lado-com-reset * {
            box-sizing: border-box; /* O recheio e a borda ficam DENTRO dos 300px */
            margin: 0;              /* Zera o espaço por fora padrão */
            padding: 0;             /* Zera o espaço por dentro padrão */
        }

        /* ==========================================================================
           ESTILOS DO LAYOUT DA PÁGINA (Para deixar o projeto bonito)
           ========================================================================== */
        body {
            font-family: 'Segoe UI', Arial, sans-serif;
            background-color: #f4f7f6;
            color: #333;
            padding: 40px 20px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        header {
            text-align: center;
            margin-bottom: 40px;
            max-width: 600px;
        }

        header h1 {
            color: #2c3e50;
            margin-bottom: 10px;
        }

        .container-comparacao {
            display: flex;
            gap: 40px;
            flex-wrap: wrap;
            justify-content: center;
        }

        .coluna {
            background: white;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 4px 15px rgba(0,0,0,0.05);
            width: 360px;
        }

        .coluna h2 {
            font-size: 1.2rem;
            margin-bottom: 15px;
            text-align: center;
            padding-bottom: 10px;
            border-bottom: 2px solid #eee;
        }

        .coluna-padrao h2 { color: #e74c3c; }
        .coluna-reset h2 { color: #2ecc71; }

        /* Linha guia cinza para mostrar o limite máximo que a caixa DEVERIA ter (300px) */
        .guia-tamanho {
            width: 300px;
            border: 2px dashed #bbb;
            background-color: #fafafa;
            margin-bottom: 20px;
            padding: 10px 0;
            text-align: center;
            font-size: 0.85rem;
            color: #777;
        }

        /* ==========================================================================
           A PROVA REAL: CONFIGURAÇÃO DAS DUAS CAIXAS
           Ambas dizem ter width: 300px, padding: 25px e border: 10px
           ========================================================================== */
        
        /* CAIXA 1: Padrão do Navegador (Content-Box) */
        .caixa-padrao {
            width: 300px;
            padding: 25px;
            border: 10px solid #e74c3c;
            background-color: #ffdddd;
            
            /* O navegador calcula: 300px + 50px(padding) + 20px(borda) = 370px real! */
        }

        /* CAIXA 2: Com Border-Box (Graças ao Reset colocado lá no topo) */
        .caixa-com-reset {
            width: 300px;
            padding: 25px;
            border: 10px solid #2ecc71;
            background-color: #d5f5e3;

            /* O navegador calcula: Tudo espremido dentro dos 300px. Real = 300px! */
        }

        /* Detalhes internos das caixas */
        .conteudo-caixa {
            background-color: rgba(255, 255, 255, 0.7);
            padding: 10px;
            font-weight: bold;
            text-align: center;
        }
    </style>
</head>
<body>

    <header>
        <h1>Demonstração Prática do Box-Sizing</h1>
        <p>Ambas as caixas abaixo foram configuradas no código com a largura de <strong>300px</strong>. Veja o que acontece quando adicionamos recheio (padding) e moldura (border).</p>
    </header>

    <div class="container-comparacao">

        <div class="coluna coluna-padrao">
            <h2>Estilo Padrão (Sem Reset)</h2>
            
            <div class="guia-tamanho">O limite correto é este espaço (300px)</div>
            
            <div class="caixa-padrao">
                <div class="conteudo-caixa">
                    Eu "engordei"! <br>
                    Meça de ponta a ponta: tenho 370px reais. 
                </div>
            </div>
        </div>

        <div class="coluna coluna-reset lado-com-reset">
            <h2>Com Reset (Border-Box)</h2>
            
            <div class="guia-tamanho">O limite correto é este espaço (300px)</div>
            
            <div class="caixa-com-reset">
                <div class="conteudo-caixa">
                    Eu me comportei! <br>
                    Continuo exatamente com os 300px definidos.
                </div>
            </div>
        </div>

    </div>

</body>
</html>
