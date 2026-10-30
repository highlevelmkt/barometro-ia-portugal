# Barómetro HLM: quem as IAs recomendam na sua cidade

Dados abertos do Barómetro HLM, um estudo da High Level Marketing (HLM) sobre as empresas locais que o ChatGPT, o Perplexity e o Resumo de IA do Google recomendam em cidades portuguesas.

Relatório: https://www.highlevelmkt.com/relatorios/barometro-ia-quem-as-ias-recomendam-2026-10

## Edição n.º 1 (29/10/2026)

- **Perguntas:** «Quem faz remodelações de casas em [cidade]? Recomende 3 empresas.» e «Preciso de um eletricista em [cidade]. Que empresas recomenda?». No Porto usou-se «no Porto».
- **Cidades:** Lisboa, Setúbal, Leiria, Porto e Aveiro.
- **Motores:** Google com o Resumo de IA (`google.pt`, `hl=pt-PT`), ChatGPT (chatgpt.com, sem sessão, pesquisa web activa) e Perplexity (sem sessão).
- **Quando:** 29/10/2026, das 17:29 às 17:43, hora de Lisboa. Foram 30 perguntas, todas com resposta.
- **Onde:** um browser, sem sessão iniciada, a partir de um IP em São Domingos de Rana (Grande Lisboa). O Google ignora o parâmetro de localização `uule`, por isso não foi possível pesquisar a partir de cada cidade.

### Ficheiros

| Ficheiro | Conteúdo |
|---|---|
| `dados/barometro-01-2026-10-29.csv` | Uma linha por empresa recomendada (`tipo=recomendacao`, 94 linhas) e por lugar no top 3 do mapa do Google (`tipo=mapa_top3`, 27 linhas). |
| `dados/barometro-01-2026-10-29-resumo-cidades.json` | Totais por cidade, ofício e motor. |

### Campos do CSV

- `corrida`: n.º da pergunta (1–30). `motor`: `google_resumo_ia`, `chatgpt` ou `perplexity`.
- `resumo_ia_presente`, `mapa_presente`: se o Google mostrou o Resumo de IA ou o mapa local (1/0; vazio fora do Google).
- `plataformas_recomendadas`: plataformas de orçamentos que a resposta mandou consultar, separadas por `|`.
- `empresa_id`: código anónimo e estável dentro da edição. A mesma empresa tem o mesmo código em todas as respostas.
- `fonte_tipo`, de onde veio a recomendação:
  - `pagina_servico_cidade`: página do site da empresa sobre aquele serviço naquela cidade;
  - `site_proprio`: outra página do site da empresa;
  - `ficha_google`: Perfil da Empresa no Google;
  - `dados_mapa_sem_fonte`: cartão com nota e morada, sem fonte indicada;
  - `diretorio`: plataforma de orçamentos (Zaask, Fixando, Habitissimo, CustoJusto);
  - `listicle`: artigo «as melhores empresas».
- `pagina_servico_cidade`: a página citada fala daquele serviço naquela cidade (1), não fala (0), ou não foi possível identificar a página (`nd`).
- `fonte_inferida`: 1 quando o ChatGPT não indicou a fonte, mas a nota, o n.º de avaliações e a morada eram iguais aos do mapa do Google na mesma pergunta.
- `nota`, `avaliacoes_banda` (1-9, 10-49, 50-199, 200+), `nota_origem`: a nota e o volume de avaliações, e de onde vieram.

### Limites

É uma fotografia de um dia, com uma pergunta por motor. As respostas das IAs mudam de pessoa para pessoa e de dia para dia. Com 94 recomendações, diferenças de poucos pontos não têm significado. Cobre só 2 ofícios e 5 cidades. Os nomes das empresas não são publicados; uma das empresas recomendadas é cliente da HLM, o que não teve qualquer efeito na recolha.

## Licença e citação

Os dados estão sob a licença [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.pt). Pode usá-los e citá-los com a fonte:

> High Level Marketing (2026). *Barómetro HLM: quem as IAs recomendam na sua cidade, n.º 1* [Conjunto de dados]. Recolha de 29/10/2026.

---

## English summary

Open data from the HLM Barometer, a study of which local businesses ChatGPT, Perplexity and Google's AI Overviews recommend in Portuguese cities (electricians and home renovation; Lisbon, Setúbal, Leiria, Porto, Aveiro; 30 queries on 29 Oct 2026, logged-out). Only 8 of 86 recommended businesses (9%) were named by two engines for the same query, and none by all three. Business names are replaced by anonymous IDs. Licence: CC BY 4.0.
