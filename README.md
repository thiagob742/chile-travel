# Roteiro Chile — 30/06 → 14/07/2026

Roteiro interativo de viagem ao Chile (Santiago + arredores) em formato Trello, com drag-and-drop para reorganização, persistência local, e todos os custos em R$.

## Como abrir

1. Dê duplo-clique em **`index.html`** — abre direto no navegador (Chrome ou Edge recomendados).
2. Não precisa instalar nada. Tudo roda via CDN (Tailwind, SortableJS, Lucide).
3. Funciona offline depois de carregado uma vez.

## O que tem

- **📋 Roteiro** — 15 colunas (uma por dia), cards arrastáveis entre dias e dentro do dia.
- **💰 Orçamento** — total geral, por categoria, e por dia (recalcula sozinho).
- **✅ Checklist** — itens pré-viagem (documentos, reservas, cadenas de neve...).
- **🗺️ Mapa** — mapa de referência + atalhos para rotas principais.
- **ℹ️ Como usar** — guia rápido.

## Estrutura dos cards

| Tipo | O que aparece |
|------|---------------|
| 🛬 Logística | Voos, transfers, check-in/out |
| 🏔️ Neve | Parque, ski-pass, horário |
| 🏛️ Atração | Museu/atração + ingresso + horário |
| 🍽️ Refeição | Restaurante + link cardápio + custo |
| ☕ Lanche | Café/sorvete/sopaipilla |
| 📷 Foto | Mirante específico + dica de luz |
| 🅿️ Estacionamento | Endereço + preço estimado |
| 🌅 Sunset | Pôr do sol + horário (gradient) |
| 🚗 Deslocamento | Trajeto + tempo + pedágio |
| 🍷 Vinícola | Tour + degustação + custo |
| ♨️ Termas | Acesso + preço + dicas |
| 🛍️ Compras | Souvenirs, vinhos, eletrônicos |

Cada card tem (quando aplicável):
- **📍 Maps** — link direto Google Maps
- **🔗 Site** — site oficial
- **📋 Cardápio** — para restaurantes
- **💰** custo para 1 pessoa **e** para o casal
- **💡** dica/observação

## Reorganizar o roteiro

- **Arrastar e soltar** entre colunas (dias) ou dentro da mesma coluna.
- Tudo persiste automaticamente no `localStorage` do navegador.
- **🔄 Resetar ordem** (botão no topo) volta ao roteiro original.
- **📥 Exportar JSON** baixa um arquivo com a versão atual personalizada.

## Editar valores ou conteúdo

Tudo está em **`data/itinerary.js`**. Cada card é um objeto JS:

```js
{
  id: "d1-7",
  type: "meal",
  time: "13:45",
  duration: "1h30",
  title: "Almoço — Mercado Central",
  location: "Mercado Central",
  mapsUrl: "https://...",
  url: "https://...",
  menuUrl: "https://...",
  costPP: 130,        // R$ por pessoa
  costCouple: 260,    // R$ casal
  notes: "Pedir caldillo de congrio..."
}
```

Edite o `.js`, salve, recarregue a página com **`Ctrl+F5`** (limpar cache).

> ⚠️ Se você já reorganizou cards e quiser ver as edições na ordem original, clique em **🔄 Resetar ordem** primeiro.

## Câmbio

Todos os valores foram convertidos com **R$ 1 = 175 CLP** (maio/2026).

**Revalide a cotação 1 semana antes** da viagem em:
- https://wise.com/us/currency-converter/brl-to-clp-rate
- https://br.investing.com/currencies/brl-clp

Se a cotação variar bastante, ajuste a constante `rateBRLtoCLP` no início de `data/itinerary.js` e refaça os cálculos.

## Imprimir o roteiro

`Ctrl+P` na aba **Roteiro**. O CSS de impressão expande todas as colunas verticalmente.

## Resumo do orçamento (casal — calculado dinamicamente na aba 💰)

| Categoria | R$ aprox (casal) |
|-----------|------------------|
| Refeições (jantares + almoços) | ~4.770 |
| Neve (3 dias: pass + equipamento) | ~2.400 |
| Vinícolas (Casas del Bosque + Matetic + Concha y Toro) | ~1.470 |
| Boragó (último jantar — opcional) | ~1.500 |
| Atrações pagas (museus + Sky + funicular + Neruda) | ~530 |
| Lanches + cafés | ~720 |
| Deslocamentos + pedágios | ~580 |
| Estacionamentos | ~330 |
| Compras/souvenirs | ~600 |
| Logística (mercado, etc) | ~280 |
| **TOTAL ESTIMADO** | **~R$ 15.100** |
| Média por dia (casal) | ~R$ 1.007 |

*Não inclui voo internacional nem aluguel do carro (já contratados).*

> 💡 Removendo o **Boragó** (R$ 1.500) do D13, a média baixa para **~R$ 906/dia** (dentro do orçamento médio R$ 600-1.000). Boragó é o jantar mais caro — restaurante TOP 50 do mundo. Alternativa indicada nos notes do card: **99 Restaurante** (CLP 80k pp ≈ R$ 457 pp).

## Reservas com antecedência

| Atração | Antecedência | Link |
|---------|--------------|------|
| Boragó (D13) | 2-3 MESES | https://www.borago.cl/ |
| Casas del Bosque (D7) | 15+ dias | https://www.casasdelbosque.cl/ |
| Matetic (D7) | 15+ dias | https://www.matetic.com/ |
| Concha y Toro (D10) | 7 dias | https://conchaytoro.com/wineandvisitors/ |
| La Moneda tour (D8) | 7+ dias | https://www.gob.cl/visita-la-moneda/ |
| Sky Costanera Sunset (D1) | dia anterior | https://www.skycostanera.cl/ |
| Restaurantes premium (Mulato, Peumayen) | 1 semana | links nos cards |

## Estrutura de arquivos

```
chile-travel/
├── index.html              # Página principal
├── data/
│   └── itinerary.js        # Dados do roteiro (15 dias)
├── assets/
│   └── styles.css          # Estilos extras
├── .claude/
│   └── skills/
│       └── travel-planner/ # Skill instalada
└── README.md
```

## Tecnologia

- **HTML5** + **Tailwind CSS** (via CDN)
- **SortableJS** para drag-and-drop
- **Lucide Icons** para ícones
- **Vanilla JS** + `localStorage` (sem build, sem servidor)
