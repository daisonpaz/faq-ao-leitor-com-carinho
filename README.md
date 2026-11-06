# FAQ — Ao Leitor com Carinho

Página única em HTML com perguntas e respostas sobre o editor **Eric** e a editora **Ao Leitor com Carinho**: história, motivações, métodos de trabalho, estratégias de publicação, a diferença entre pirataria e publicação não licenciada, o domínio público na Era de Ouro dos quadrinhos e curiosidades.

O conteúdo foi compilado a partir de duas fontes em vídeo (transcrições): uma entrevista com o editor e uma reportagem sobre a coleção de *Spirit*. O texto é uma síntese em palavras próprias, não uma reprodução das transcrições.

## Sumário

- [Visão geral](#visão-geral)
- [Estrutura do projeto](#estrutura-do-projeto)
- [Como visualizar](#como-visualizar)
- [Publicar no GitHub Pages](#publicar-no-github-pages)
- [Conteúdo da página](#conteúdo-da-página)
- [Como editar o conteúdo](#como-editar-o-conteúdo)
- [Design e personalização](#design-e-personalização)
- [Aviso sobre o conteúdo jurídico](#aviso-sobre-o-conteúdo-jurídico)
- [Licença](#licença)

## Visão geral

| Item | Detalhe |
|---|---|
| Tecnologia | HTML, CSS e JavaScript puro (sem frameworks, sem build) |
| Arquivos | 1 arquivo HTML autocontido |
| Idioma | Português do Brasil (`pt-BR`) |
| Dependências externas | Google Fonts (Anton, PT Serif, Special Elite) |
| Interatividade | Acordeão nativo (`<details>`) e filtro por categoria |
| Responsivo | Sim, com ajuste para telas até 540 px |

## Estrutura do projeto

```
.
├── index.html     # a página (renomeie de faq-ao-leitor-com-carinho.html)
└── README.md      # esta documentação
```

> Para o GitHub Pages servir a página na raiz do site, o arquivo precisa se chamar `index.html`.

## Como visualizar

Localmente, basta abrir o arquivo no navegador (duplo clique). Não há servidor nem instalação.

Se preferir um servidor local:

```bash
python3 -m http.server 8000
# acesse http://localhost:8000
```

> As fontes vêm do Google Fonts, então é necessária conexão com a internet para o visual completo. Sem ela, o navegador usa fontes substitutas (serifa e monoespaçada do sistema).

## Publicar no GitHub Pages

1. Crie um repositório no GitHub (por exemplo, `faq-ao-leitor-com-carinho`).
2. Envie os arquivos:

   ```bash
   git init
   git add index.html README.md
   git commit -m "Primeira versão do FAQ"
   git branch -M main
   git remote add origin https://github.com/SEU-USUARIO/faq-ao-leitor-com-carinho.git
   git push -u origin main
   ```

3. No repositório, abra **Settings → Pages**.
4. Em **Build and deployment**, escolha **Deploy from a branch**, selecione a branch `main` e a pasta `/ (root)`, e salve.
5. Após alguns minutos, a página ficará em:
   `https://SEU-USUARIO.github.io/faq-ao-leitor-com-carinho/`

## Conteúdo da página

A página tem sete categorias, cada uma com perguntas em formato de acordeão:

| # | Categoria | `data-cat` | O que cobre |
|---|---|---|---|
| 01 | História e motivações | `historia` | Quem é o editor, por que virou editor, origem do nome da editora, como começou sem contatos, o lançamento sem licença e a repercussão |
| 02 | Objetivo da editora | `objetivo` | Resgate de material inédito ou esquecido e foco fora do mainstream |
| 03 | Métodos de trabalho | `metodos` | Restauração, produção solo, vendas e entrega |
| 04 | Estratégias de publicação | `estrategias` | Nomes Gibi Mensal e Lobinho, coleções planejadas, coleção *Spirit*, planos futuros |
| 05 | Pirataria x não licenciado | `pirataria` | Diferença conceitual e o caso do primeiro mangá |
| 06 | Era de ouro | `era-de-ouro` | Domínio público, limites de uso de personagens, regra Brasil–EUA, caso *Spirit* |
| 07 | Curiosidades | `curiosidades` | Origem de "gibi", Super Mouse, método de tradução, editora semelhante nos EUA |

## Como editar o conteúdo

### Adicionar uma pergunta

Dentro da `<section>` da categoria desejada, acrescente um bloco `<details>`:

```html
<details class="qa">
  <summary>Sua pergunta aqui?</summary>
  <div class="a">
    <p>Sua resposta aqui.</p>
  </div>
</details>
```

Dentro de `.a` é possível usar `<p>`, `<ul>`/`<li>`, `<strong>` (destaque em vermelho) e `<em>`.

Para que uma pergunta já comece aberta, adicione o atributo `open`: `<details class="qa" open>`.

### Adicionar uma categoria

1. Copie uma `<section class="category" data-cat="...">` inteira e dê um novo valor a `data-cat`.
2. Adicione um botão correspondente em `<div class="filters">`, com o mesmo valor em `data-filter`:

   ```html
   <button data-filter="nova-categoria">Nome da categoria</button>
   ```

3. (Opcional) Defina a cor do número da categoria no CSS:

   ```css
   .category[data-cat="nova-categoria"] .category-num{ background: var(--blue); }
   ```

O script no final do arquivo cuida do filtro automaticamente, sem alterações.

## Design e personalização

O visual lembra uma revista em quadrinhos antiga: papel envelhecido, trama de pontos (*halftone*), bordas grossas com sombra sólida.

As cores ficam em variáveis CSS no topo do `<style>`:

| Variável | Uso |
|---|---|
| `--paper` / `--paper-2` | Fundo da página e dos painéis |
| `--ink` / `--ink-soft` | Texto e bordas |
| `--red` | Destaques, selo e números de categoria |
| `--blue` | Categorias de métodos e estratégias |
| `--yellow` | Categoria de curiosidades e detalhes |
| `--rule` | Linhas finas divisórias |

Fontes: **Anton** (títulos), **PT Serif** (texto) e **Special Elite** (detalhes em máquina de escrever).

## Aviso sobre o conteúdo jurídico

As seções sobre domínio público, licenciamento e marcas descrevem o que foi dito pelo editor e pelos entrevistados nas fontes originais. **Não constituem aconselhamento jurídico.** O próprio advogado citado na reportagem classificou a publicação de *Spirit* como um "risco calculado", ou seja, há margem de incerteza. Para decisões práticas, consulte um profissional especializado em propriedade intelectual.

## Licença

Defina a licença conforme sua preferência antes de publicar. Sugestões comuns:

- **MIT**: livre para uso e modificação do código da página.
- **CC BY 4.0**: indicada se você quiser permitir reuso do texto com atribuição.

Lembre-se de que o conteúdo é derivado de entrevistas e reportagens de terceiros; mantenha a atribuição das fontes originais se redistribuir o texto.
