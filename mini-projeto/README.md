# Oceano 

Uma animação 2D de um fundo do mar, feita em Canvas + JavaScript puro. Um estudo de transformações geométricas (translação, rotação, escala e reflexão).

## Grupo
- [Bento Guilherme Gomes Oliveira](https://github.com/bnnto)
- [Lorenna Meneses de Almeida](https://github.com/lorennam)

## Como rodar

É só abrir no VSCode com Integrated Browser ou a extensão Live Server.

## Controles

- Clicar na tela → solta várias bolinhas
- F → adiciona um peixe novo
- M → espelha a cena inteira
- Espaço → pausa/despausa a animação
- R → reseta a cena

## Requisitos do projeto

| # | Requisito | Onde está |
|---|---|---|
| 1 | Translação (`ctx.translate`) | Em quase tudo: posiciona o baú, a pedra, cada peixe, cada bolha e cada segmento de alga na cena |
| 2 | Rotação (`ctx.rotate`) | Tampa do baú abrindo/fechando, cauda dos peixes balançando, peixe se inclinando ao nadar, algas balançando segmento por segmento |
| 3 | Escala (`ctx.scale`) | Pedra pulsando, bolha crescendo enquanto sobe, peixe redimensionado conforme o `tam` sorteado, cada segmento de alga fica menor que o anterior |
| 4 | Composição de transformações | O peixe é o exemplo mais claro: `translate` → `scale` → `rotate` antes de desenhar. As algas também: cada volta do laço soma `rotate` + `translate` + `scale` |
| 5 | Rotação/escala com ponto fixo (T → Op → T) | Tampa do baú gira em torno da dobradiça, (`translate` até a dobradiça → `rotate` → `translate` de volta). A pedra escala em torno do próprio centro do mesmo jeito |
| 6 | Animação com `requestAnimationFrame` + reset de matriz | Função `animar()`: começa sempre com `ctx.setTransform(1,0,0,1,0,0)` e termina chamando `requestAnimationFrame(animar)` de novo |
| 7 | save/restore ou setTransform | Usado o tempo todo — cada objeto (baú, pedra, cada peixe, cada bolha, cada alga) fica isolado dentro do seu próprio `ctx.save() / ctx.restore()`, pra não vazar transformação de um pro outro |

**Bônus:**
- **Interatividade**: clique do mouse solta bolhas onde você clicar; teclado controla tudo (F, M, Espaço, R)
- **Reflexão**: tecla M espelha a cena inteira no eixo X (`translate` até a borda + `scale(-1, 1)`)