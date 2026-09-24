# Clubes em Números

Site com a análise financeira dos clubes brasileiros a partir das demonstrações financeiras oficiais publicadas por cada clube, de 2020 a 2025. Todos os valores estão em milhares de reais.

Endereço: https://sice07.github.io/Clubes/

## Estrutura

```
index.html        hub, com a seleção por escudo e o comparativo
capa.png          imagem de prévia para redes sociais
fluminense/       painel completo do clube
flamengo/
palmeiras/
vasco/
saopaulo/
santos/
gremio/
internacional/
athletico/
coritiba/
chapecoense/
```

Cada pasta de clube tem o painel em `index.html` e a própria `capa.png`. Os painéis são páginas independentes, sem dependência externa, e trazem um link de volta para o hub na barra lateral.

## Como publicar

1. Criar o repositório `Clubes` no GitHub e subir esta pasta inteira.
2. Em Settings, Pages, apontar a origem para a branch principal e a raiz do repositório.
3. O site fica no ar em https://sice07.github.io/Clubes/ em alguns minutos.

## Como entra um clube novo

1. Criar a pasta do clube com o painel dele em `index.html` e uma `capa.png` de 1200 por 630.
2. No `index.html` do hub, procurar a lista `CLUBES` e trocar a linha do clube para `dados:true`, apontando `url` para a pasta nova. A cor e a forma do marcador vêm da posição na seleção, então não há nada a escolher.
3. Acrescentar a chave do clube no objeto `DATA`, no mesmo formato dos outros, e refazer o agregado `br` somando os clubes mapeados. O agregado guarda em `clubesAno` quantos clubes entraram na soma de cada ano, e um clube sem o balanço aberto por prazo fica de fora dele até a linha chegar.

O hub se ajusta sozinho depois disso, incluindo a contagem de clubes, o mapa, o desenho da abertura e o comparativo.

## Sobre o mapa

O mapa traz o contorno real dos estados, vindo do projeto svg-maps em licença Creative Commons BY 4.0, com o traçado simplificado para o arquivo ficar leve. Cada estado fica mais forte conforme o número de clubes dali com painel publicado, e clicar num estado ou numa região monta a seleção do comparativo. Estados estreitos demais para a sigla caber dentro recebem a etiqueta ao lado, com um fio ligando ao estado, e essa lista fica na constante `UF_FORA`.

## As sete abas

O relatório abre sempre na **Resumida**, que começa com um cartão sobre o projeto e segue com o essencial em linguagem simples. A **Comparativa** traz o quadro completo de indicadores com o gráfico de evolução e uma ficha por clube. A **Receita** mostra de onde vem o dinheiro de cada clube. O **Endividamento** mostra o que o clube deve e para quem. **Sócio e bilheteria** isola as duas fontes que dependem direto do torcedor. **Patrocínio** mede o que a marca do clube rende e compara com a cota de televisão. O **Ranking** ordena todos os clubes mapeados em seis listas, três de receita e três de dívida, e fecha com as posições lado a lado.

A escolha de clubes fica acima das abas e vale para todas. Já são mais clubes mapeados do que cabem na seleção, que é de oito. Clicar num nono tira o mais antigo, e escolher uma região inteira deixa os oito maiores em receita do ano. O limite de oito é o limite da paleta, que passa no teste de daltonismo com essas oito cores e não com mais. Trocar de aba leva o leitor direto para o conteúdo dela.

As quatro abas de tema usam o mesmo desenho de barras: a largura compara o tamanho entre clubes e os pedaços mostram a composição de cada um. Em sócio e bilheteria e em patrocínio a barra inteira é a receita total do clube e os pedaços coloridos são o tema da aba, com o resto da arrecadação em cinza, só para dar a escala. Nessas duas o rótulo da linha traz o valor do tema e a fatia que ele representa, e o pedaço cinza fica sem rótulo de propósito, para o olho não ler o número errado. A dívida é aberta em bancos, tributos parcelados e o restante, que reúne fornecedores, compra de atletas, antecipações e demais obrigações.

As duas trazem o quadro de indicadores do assunto e um parágrafo montado a partir dos próprios números, que diz o que o quadro mostra naquele ano. O bloco de barras que fica junto da seleção acompanha a aba aberta, mostrando receita, dívida, dinheiro da torcida ou patrocínio conforme o caso. Já a aba de ranking considera sempre todos os clubes mapeados, e não apenas os escolhidos, que aparecem lá com a cor da seleção. A Comparativa traz também uma ficha por clube, com receita, dívida e resultado do ano, a variação contra o ano anterior e o caminho para o painel completo.

## Critérios

Os indicadores seguem o cálculo de cada painel individual, então o número do hub é o mesmo que aparece ao abrir o clube. O que o clube deve é sempre o passivo exigível, circulante mais não circulante. O Brasileirão é a soma dos clubes já mapeados, com os índices recalculados sobre os totais, e fica sem valor no ano em que algum clube não publica a linha. A soma de cada ano leva só os clubes que publicaram aquele ano, e quantos foram fica guardado em `clubesAno` e aparece no KPI do topo.

Os clubes não abrem as contas do mesmo jeito. O Palmeiras publica a receita já líquida de impostos, o Vasco tem 2020 e 2021 da associação e apenas cinco meses em 2022 por causa da criação da SAF, e São Paulo e Santos informam as deduções da receita em linha separada, além de publicarem no balanço o total do ativo no lugar do exigível, o que o hub corrige somando circulante e não circulante. O Grêmio é associação em toda a série e mudou a apresentação em 2024, quando a venda de atletas saiu da receita do desporto e a loja e os royalties entraram nela, e o hub põe os seis anos no mesmo critério, com os ganhos contábeis da Arena fora da receita e do EBITDA. No Internacional, no Athletico-PR, no Coritiba e na Chapecoense as deduções da receita vêm em linha separada e são rateadas entre as cinco fontes operacionais, então a receita operacional do quadro é a líquida e ela mais as transferências dão exatamente a receita total. O Coritiba publica no formato comparável a partir de 2022, quando as contas passam a ser da SAF. Na Chapecoense o ganho contábil da recuperação judicial em 2023 fica fora da receita e do EBITDA. No Athletico-PR a dívida bancária é o financiamento da Arena e no Coritiba o parcelamento com o Banco Central entra em bancos, porque é empréstimo. A linha de tributos é sempre só o que está parcelado, e a obrigação tributária corrente entra no restante do exigível. As comparações mostram ordem de grandeza e tendência, não diferença exata.

Dados e desenvolvimento: Victor Belchior.
