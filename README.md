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
```

Cada pasta de clube tem o painel em `index.html` e a própria `capa.png`. Os painéis são páginas independentes, sem dependência externa, e trazem um link de volta para o hub na barra lateral.

## Como publicar

1. Criar o repositório `Clubes` no GitHub e subir esta pasta inteira.
2. Em Settings, Pages, apontar a origem para a branch principal e a raiz do repositório.
3. O site fica no ar em https://sice07.github.io/Clubes/ em alguns minutos.

## Como entra um clube novo

1. Criar a pasta do clube com o painel dele em `index.html` e uma `capa.png` de 1200 por 630.
2. No `index.html` do hub, procurar a lista `CLUBES` e trocar a linha do clube para `dados:true`, apontando `url` para a pasta nova, com uma cor de série e uma forma de marcador livres.
3. Acrescentar a chave do clube no objeto `DATA`, no mesmo formato dos outros, e refazer o agregado `br` somando os clubes mapeados.

O hub se ajusta sozinho depois disso, incluindo a contagem de clubes, o desenho da abertura e o comparativo.

## Critérios

Os indicadores seguem o cálculo de cada painel individual, então o número do hub é o mesmo que aparece ao abrir o clube. O que o clube deve é sempre o passivo exigível, circulante mais não circulante. O Brasileirão é a soma dos clubes já mapeados, com os índices recalculados sobre os totais, e fica sem valor no ano em que algum clube não publica a linha.

Os clubes não abrem as contas do mesmo jeito. O Palmeiras publica a receita já líquida de impostos, o Vasco tem 2020 e 2021 da associação e apenas cinco meses em 2022 por causa da criação da SAF, e o São Paulo informa as deduções da receita em linha separada. As comparações mostram ordem de grandeza e tendência, não diferença exata.

Dados e desenvolvimento: Victor Belchior.
