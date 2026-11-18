# Naomi Arakaki · Portfólio

## Estrutura da página

| Seção | Âncora | Conteúdo |
|---|---|---|
| Hero | `#topo` | Proposta de valor, links (LinkedIn, GitHub) e um terminal com o método em pseudocódigo Python |
| Sobre | `#sobre` | Três pilares: IA aplicada, engenharia e automação, produto e estratégia |
| Projetos | `#projetos` | Quatro cases com filtro por categoria. Cada um abre um modal com o detalhe |
| Habilidades | `#skills` | Ferramentas agrupadas em IA &amp; LLM, linguagens, dados, cloud, observabilidade e produto |
| Trajetória | `#exp` | Linha do tempo: Amazon (BI Intern), Circana (Market Intelligence Intern) e pesquisa acadêmica |
| Formação | `#formacao` | Mackenzie (Sistemas de Informação), AWS Cloud Foundations e idiomas |
| Contato | `#contato` | E-mail, LinkedIn e GitHub |

### Cases

| ID | Case | Tags de filtro |
|---|---|---|
| `c1` | Automação de disputas de cobranças, com KPIs, arquitetura de gates, método reutilizável e próximos passos com IA | `eng` `prod` `ia` |
| `c2` | Agente de inteligência de mercado (prompt em camadas, guardrails, chain-of-verification) | `ia` |
| `c3` | Process data: pipeline em Python e análise em R (LCS, modelos mistos, n-gramas) | `dados` `eng` |
| `c4` | Pricing e requisitos de produto (P&amp;L unitário, benchmark, BRD) | `prod` `dados` |

---

## Funcionalidades

- **Roteamento por hash:** cada case tem uma URL própria (`#case/c1` … `#case/c4`). O link pode ser compartilhado, o botão Voltar do navegador fecha o modal e recarregar a página abre o mesmo case.
- **Modal nativo** com `<dialog>`. Fecha com ✕, com `Esc` ou com um clique fora da janela.
- **Filtro de projetos** por categoria: IA &amp; LLM, Engenharia, Dados &amp; Estatística e Produto &amp; Estratégia.
- **Tema claro ou escuro:** segue `prefers-color-scheme` e tem um botão ◐ que guarda a escolha em `localStorage`.
- **Menu ativo:** um `IntersectionObserver` destaca a seção visível.
- **Acessibilidade:** os cards abrem com `Enter` ou `Espaço`, têm foco visível e respeitam `prefers-reduced-motion`.
- **Responsiva:** o menu é ocultado abaixo de 960px e os grids usam `auto-fit`.

---

## Como editar

Todo o conteúdo fica no próprio HTML.

### Adicionar um case

1. Crie o card dentro de `#cases`:

   ```html
   <article class="card case" data-tags="ia eng" data-case="c5" tabindex="0">
     <div class="ic">🚀</div><h3>Título do case</h3>
     <p>Resumo em uma ou duas frases.</p>
     <div class="chips"><span class="chip">Python</span></div>
     <div class="meta"><span><i class="dot" style="background:var(--ac)"></i>Status</span><span class="more">Ver case →</span></div>
   </article>
   ```

2. Crie o detalhe em um `<template>` com o mesmo ID:

   ```html
   <template id="c5">
     <h4>Contexto</h4><p>…</p>
     <h4>Solução</h4><ul><li>…</li></ul>
   </template>
   ```

   Dentro do template, você pode usar os blocos `.kpis` / `.kpi` (indicadores), `.steps` (passos numerados) e `<pre>` (diagramas ou código).

### Identidade visual

A estética mistura grid suíço com interface de dados. A ideia é parecer um painel de controle editorial:

- cantos retos, bordas sólidas de 2px e cards encostados uns nos outros, formando uma grade única;
- linhas verticais de 12 colunas ao fundo da página;
- seções numeradas (`01`, `02`…) com uma régua horizontal;
- títulos em grotesca pesada, condensada e em caixa alta;
- rótulos, filtros e datas em fonte monoespaçada;
- destaque em **lima** com efeito de marca-texto e acento em **azul elétrico**;
- um ticker de competências rolando abaixo do hero;
- um terminal com barra azul e indicador "LIVE";
- no hover, a cor do elemento se inverte, em vez de ganhar sombra.

### Mudar cores

As cores ficam em variáveis CSS no `:root` (tema escuro) e em `[data-theme="light"]` (tema claro):

| Variável | Uso |
|---|---|
| `--hl` / `--hlfg` | Marca-texto (lima) e a cor do texto sobre ele |
| `--ac` | Acento principal (lima no escuro, azul no claro) |
| `--ac2` | Acento secundário (azul elétrico) |
| `--bg` / `--bg2` | Fundo da página / fundo dos cards |
| `--fg` / `--mut` | Texto principal / texto secundário |
| `--bd` / `--ln` | Bordas / linhas do grid de fundo |

### Tipografia

- **Títulos e texto:** Helvetica Neue, com Arial Nova ou Arial como alternativa.
- **Rótulos e código:** JetBrains Mono, com Cascadia Mono ou Consolas como alternativa.

Para garantir que todo visitante veja a JetBrains Mono, adicione esta linha ao `<head>`:

```html
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@500;600;700&display=swap" rel="stylesheet">
```

---

## Confidencialidade

Os cases vêm de trabalho profissional e foram **anonimizados** antes da publicação:

- nomes internos de programas, sistemas, ferramentas, equipes e colegas foram removidos ou trocados por termos genéricos;
- concorrentes não são citados pelo nome;
- valores financeiros e métricas de negócio dos documentos estratégicos foram omitidos;
- os resultados da automação aparecem **arredondados** ou em ordem de grandeza;
- não há fotos ou identificadores corporativos (crachá, alias interno).

Os nomes das empresas aparecem apenas em Trajetória, como já constam no perfil público do LinkedIn.

> Antes de publicar qualquer atualização, revise o texto novo com o mesmo critério: um conteúdo publicado na internet pode ser indexado e guardado em cache mesmo depois de removido.

---

## Arquivos de origem

| Fonte | Uso no portfólio |
|---|---|
| Comunicado de lançamento da automação | Base do case `c1` |
| Apresentação sobre o design do agente | Base do case `c2` |
| Relatório de aprendizados da pesquisa | Base do case `c3` |
| Documentos estratégicos de pricing | Base do case `c4` (apenas métodos, sem números) |
| Perfil do LinkedIn (PDF) | Trajetória, formação, idiomas e contato |
| Portfólio de referência | Inspiração inicial de layout |

> ⚠️ Os arquivos de origem são **confidenciais** e **não devem ser publicados** junto com o portfólio. Publique somente o HTML.

---

## Contato

- E-mail: arakakinaomi228@gmail.com
- LinkedIn: [linkedin.com/in/naomi-arakaki](https://www.linkedin.com/in/naomi-arakaki/)
- GitHub: [github.com/Nana228228](https://github.com/Nana228228)
