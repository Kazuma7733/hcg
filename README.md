# HCG · History Card Game

Site + jogo + modo online, prontos para o Netlify.

- `/`            site de apresentação
- `/jogo/`       o jogo (modos aleatório, deck, local, treino e online)
- `/api/room`    servidor das salas do modo online (Netlify Function + Netlify Blobs)

## Publicar

**Pelo GitHub (recomendado):** suba esta pasta para um repositório, no app.netlify.com escolha
"Add new site → Import an existing project", selecione o repositório e confirme. As configurações
já estão no `netlify.toml` (publish = `public`, functions = `netlify/functions`).

**Pela linha de comando:**

    npm i -g netlify-cli
    netlify login
    npm install
    netlify deploy --prod

O arrastar-e-soltar do Netlify não compila funções, então o modo online só funciona com um desses dois caminhos.

## Como o modo online funciona

Um jogador cria a sala e passa o código; o outro entra. Os dois navegadores trocam jogadas pela
função `/api/room`, que guarda as mensagens de cada sala por 15 minutos no Netlify Blobs. Cada jogador
consulta a sala a cada ~0,8 s, então há um atraso de 1 a 2 s entre uma jogada e a outra tela.
