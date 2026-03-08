<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Capy Coin - A Memecoin Mais Chill do Pântano!</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 0;
            background: linear-gradient(to bottom, #a1d4e4, #f0f8ff);
            color: #2c3e50;
            overflow-x: hidden;
        }
        header {
            background: linear-gradient(135deg, #ff6b6b, #ff8e53);
            padding: 60px 20px;
            color: white;
            position: relative;
            overflow: hidden;
        }
        .logo {
            width: 220px;
            height: auto;
            animation: float 6s ease-in-out infinite;
            filter: drop-shadow(0 10px 20px rgba(0,0,0,0.3));
        }
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-20px); }
        }
        h1 { font-size: 3.5rem; margin: 10px 0; text-shadow: 3px 3px 10px rgba(0,0,0,0.4); }
        section {
            padding: 60px 20px;
            max-width: 1100px;
            margin: 0 auto;
            opacity: 0;
            transform: translateY(40px);
            transition: opacity 0.8s ease, transform 0.8s ease;
        }
        section.visible {
            opacity: 1;
            transform: translateY(0);
        }
        #about { background: rgba(255,255,255,0.7); border-radius: 20px; margin: 20px auto; }
        #how-to-buy { background: linear-gradient(to right, #a8e063, #56ab2f); color: white; }
        #community { background: #dfe9f3; }
        .btn {
            display: inline-block;
            background: #ff3366;
            color: white;
            padding: 15px 35px;
            margin: 15px;
            border-radius: 50px;
            font-size: 1.2rem;
            text-decoration: none;
            transition: all 0.3s ease;
            box-shadow: 0 8px 15px rgba(0,0,0,0.2);
        }
        .btn:hover {
            transform: scale(1.1) rotate(2deg);
            box-shadow: 0 15px 30px rgba(255,51,102,0.4);
            background: #ff6699;
        }
        .counter {
            font-size: 2.5rem;
            font-weight: bold;
            color: #ff3366;
            margin: 20px 0;
        }
        /* Bolhas de fundo */
        .bubbles {
            position: fixed;
            top: 0; left: 0; right: 0; bottom: 0;
            pointer-events: none;
            z-index: -1;
        }
        .bubble {
            position: absolute;
            background: rgba(255,255,255,0.6);
            border-radius: 50%;
            box-shadow: 0 0 20px rgba(255,255,255,0.8);
            animation: rise linear infinite;
        }
        @keyframes rise {
            0% { transform: translateY(100vh) scale(0.5); opacity: 0.1; }
            50% { opacity: 0.8; }
            100% { transform: translateY(-150px) scale(1.2); opacity: 0; }
        }
        footer {
            background: #2c3e50;
            color: white;
            padding: 20px;
            margin-top: 40px;
        }
    </style>
</head>
<body>

    <div class="bubbles" id="bubbles"></div>

    <header>
        <img src="https://thumbs.dreamstime.com/b/cool-cartoon-capybara-wearing-sunglasses-outdoors-near-lake-cheerful-animated-stylish-relaxing-serene-surrounded-lush-433219138.jpg" 
             alt="Capy Coin Logo - Capy de óculos relaxando" class="logo">
        <h1>Capy Coin</h1>
        <p>A memecoin mais relax do blockchain. Só vibes, capivaras e gains tranquilos.</p>
        <div class="counter" id="holderCounter">0 Holders Chill</div>
    </header>

    <section id="about">
        <h2>Sobre a Capy Coin</h2>
        <p>Feita pra quem curte meme, relaxar na água e ver o portfólio flutuar devagarinho como uma capivara no rio.</p>
        <p>Tokenomics simples e transparentes: 1B total supply • 50% LP • 30% marketing & parcerias • 20% community rewards.</p>
        <a href="#" class="btn">DYOR Agora</a>
    </section>

    <section id="how-to-buy">
        <h2>Como Comprar (Fácil)</h2>
        <ol style="text-align:left; max-width:600px; margin:0 auto; font-size:1.2rem; line-height:1.8;">
            <li>Instale MetaMask / Phantom</li>
            <li>Compre SOL / ETH</li>
            <li>Vá na DEX (Raydium / Uniswap)</li>
            <li>Cole o contrato: [0x... ainda em lançamento]</li>
            <li>Swap → HODL → Relaxe com a capy</li>
        </ol>
        <a href="#" class="btn">Comprar na DEX</a>
        <p style="font-size:0.9rem; margin-top:20px;">Aviso: Memecoin volátil. Só invista o que pode perder rindo.</p>
    </section>

    <section id="community">
        <h2>Junte-se à Família Capy</h2>
        <p>Memes, giveaways, chill e quem sabe uns airdrops pra quem HODLa com amor.</p>
        <a href="https://twitter.com" class="btn">Twitter</a>
        <a href="https://t.me" class="btn">Telegram</a>
        <a href="https://discord.gg" class="btn">Discord</a>
    </section>

    <footer>
        <p>© 2026 Capy Coin • Não é conselho financeiro • Só diversão e capivaras</p>
    </footer>

    <script>
        // Fade-in ao scroll
        const sections = document.querySelectorAll('section');
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, { threshold: 0.1 });

        sections.forEach(sec => observer.observe(sec));

        // Contador fake de holders
        let count = 0;
        const counterEl = document.getElementById('holderCounter');
        const target = 12478; // número fake pra dar hype
        const interval = setInterval(() => {
            count += Math.floor(Math.random() * 80) + 20;
            if (count >= target) {
                count = target;
                clearInterval(interval);
            }
            counterEl.textContent = count.toLocaleString() + " Holders Chill";
        }, 120);

        // Bolhas animadas
        function createBubble() {
            const bubble = document.createElement('div');
            bubble.classList.add('bubble');
            const size = Math.random() * 60 + 20;
            bubble.style.width = size + 'px';
            bubble.style.height = size + 'px';
            bubble.style.left = Math.random() * 100 + 'vw';
            bubble.style.animationDuration = Math.random() * 8 + 6 + 's';
            bubble.style.animationDelay = Math.random() * 5 + 's';
            document.getElementById('bubbles').appendChild(bubble);

            setTimeout(() => bubble.remove(), 15000);
        }

        setInterval(createBubble, 400);
        // Cria algumas iniciais
        for(let i = 0; i < 15; i++) createBubble();
    </script>

</body>
</html>
