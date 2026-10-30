# Barómetro HLM: quem as IAs recomendam na sua cidade

Dados abertos de um estudo da High Level Marketing (HLM). Quando alguém pede a uma IA uma empresa local, que empresas lhe aparecem? E de onde vem cada nome? Medimos isso no ChatGPT, no Perplexity e no Resumo de IA do Google, em cidades portuguesas.

- **Relatório (fonte principal):** https://www.highlevelmkt.com/relatorios/barometro-ia-quem-as-ias-recomendam-2026-10
- **Licença dos dados:** CC BY 4.0 (ver `LICENSE`). Pode usar, adaptar e republicar, desde que cite a fonte.
- **Nomes de empresas:** não são publicados. Cada empresa tem um código anónimo.

## Edição n.º 1: o essencial

Recolha a 29/10/2026, das 17:29 às 17:43 (hora de Lisboa). Foram 30 perguntas, todas com resposta.

- **As IAs quase não concordam.** As 30 respostas deram 94 recomendações. Só 8 empresas (9 %) foram recomendadas por dois motores para a mesma pergunta e cidade. Nenhuma foi recomendada pelos três.
- **Cada motor procura num sítio diferente.**
  - **Google:** 18 das 37 recomendações (49 %) vieram de uma página do site da empresa sobre aquele serviço naquela cidade.
  - **ChatGPT:** 33 das 35 (94 %) vieram com nota, morada e telefone de fichas de mapa.
  - **Perplexity:** 13 das 22 (59 %) vieram de diretórios de orçamentos.
- **A página local conta.** Em 61 recomendações a fonte era uma página web. Em 40 delas (66 %) era uma página sobre aquele serviço naquela cidade.
- **O Resumo de IA já é a regra.** Apareceu nas 10 pesquisas feitas no Google. Só 4 das 34 recomendações do Resumo (12 %) estavam no top 3 do mapa local da mesma pesquisa.

## Método

| | |
|---|---|
| Perguntas | «Quem faz remodelações de casas em [cidade]? Recomende 3 empresas.» e «Preciso de um eletricista em [cidade]. Que empresas recomenda?» No Porto: «no Porto». |
| Cidades | Lisboa, Setúbal, Leiria, Porto e Aveiro |
| Motores | Google com o Resumo de IA (`google.pt`, `hl=pt-PT`), ChatGPT (sem sessão, pesquisa web activa) e Perplexity (sem sessão) |
| Local | Um browser, sem sessão iniciada, a partir de um IP em São Domingos de Rana (Grande Lisboa) |
| Registo | Para cada empresa recomendada: posição, tipo de fonte, se a página é sobre aquele serviço naquela cidade, e a nota no Google, se a IA a mostrou. No Google, também o top 3 do mapa local. |

O esquema de cada ficheiro está em [`dados/LEIA-ME.md`](dados/LEIA-ME.md).

## Ficheiros

| Ficheiro | Conteúdo |
|---|---|
| `dados/edicao-01/barometro-01-2026-10-29.csv` | Uma linha por empresa recomendada (94) e por lugar no top 3 do mapa do Google (27). |
| `dados/edicao-01/barometro-01-2026-10-29-resumo-cidades.json` | Totais por cidade, ofício e motor. |

## Limites

- **É uma fotografia de um dia, não um censo.** Uma pergunta por motor, à mesma hora, sem sessão e a partir de um só ponto. As respostas das IAs mudam de pessoa para pessoa e de dia para dia.
- **A amostra é pequena.** Com 94 recomendações, diferenças de poucos pontos não têm significado.
- **Cobre pouco.** Só 2 ofícios e 5 cidades.
- **Fontes por indicar.** Em 16 recomendações o ChatGPT não indicou de onde vinha a nota.
- **86 ou 85 empresas.** O relatório fala em 86 empresas: é a soma das empresas distintas em cada cidade e ofício. O CSV tem 85 códigos, porque uma empresa de Aveiro foi recomendada nos dois ofícios e tem o mesmo código nos dois.
- **Um cliente da HLM.** Uma das 94 recomendações é de um cliente da HLM, e isso não teve qualquer efeito na recolha.

## Edições

| Edição | Recolha | Estado |
|---|---|---|
| n.º 1 | 29/10/2026 | publicada (`v1.0.0`) |
| n.º 2 | 23–27/11/2026 | prevista para 30/11/2026 |

Cada edição sai numa release com o número da versão. As correcções ficam descritas na release e nunca apagam a versão anterior.

## Como citar

> High Level Marketing (2026). *Barómetro HLM: quem as IAs recomendam na sua cidade, n.º 1* [Conjunto de dados]. Recolha de 29/10/2026. https://github.com/highlevelmkt/barometro-ia-portugal

Também em `CITATION.cff` (botão «Cite this repository» do GitHub).

## Contacto

Jornalistas e investigadores: https://www.highlevelmkt.com/imprensa · geral@highlevelmkt.com. Encontrou um erro? Abra uma *issue* ou escreva-nos.

---

## English summary

Open data from the HLM Barometer, a study of which local businesses ChatGPT, Perplexity and Google's AI Overviews recommend in Portuguese cities. Edition 1 covers electricians and home renovation in Lisbon, Setúbal, Leiria, Porto and Aveiro: 30 logged-out queries on 29 Oct 2026, with 94 recommendations. Only 8 recommended businesses (9%) were named by two engines for the same query, and none by all three. Each engine relied on a different source: service-and-city pages for Google, map listings for ChatGPT and quote directories for Perplexity. Business names are replaced by anonymous IDs. Licence: CC BY 4.0. Full report (Portuguese): https://www.highlevelmkt.com/relatorios/barometro-ia-quem-as-ias-recomendam-2026-10
