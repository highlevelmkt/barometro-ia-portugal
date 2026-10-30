# Dados: esquema

Uma pasta por edição. Os ficheiros de uma edição publicada não mudam. Se houver correcção, sai um ficheiro novo e a release explica o que mudou.

```
dados/
  edicao-01/
    barometro-01-2026-10-29.csv
    barometro-01-2026-10-29-resumo-cidades.json
  edicao-02/            (a partir de 30/11/2026)
```

Formato: CSV em UTF-8, separado por vírgulas, com cabeçalho. Decimais com ponto (`4.9`). Datas em `AAAA-MM-DD`. Hora de Lisboa.

## `barometro-01-2026-10-29.csv`

Há dois tipos de linha:
- `recomendacao`: uma empresa recomendada numa resposta (94 linhas);
- `mapa_top3`: um dos 3 primeiros lugares do mapa local do Google, na mesma pesquisa (27 linhas). Serve de comparação.

| Coluna | Tipo | Valores | O que é |
|---|---|---|---|
| `edicao` | inteiro | `1` | N.º da edição do barómetro. |
| `data` | data | `2026-10-29` | Dia da recolha. |
| `motor` | texto | `google_resumo_ia`, `chatgpt`, `perplexity` | Motor que respondeu. |
| `cidade` | texto | Lisboa, Setúbal, Leiria, Porto, Aveiro | Cidade da pergunta. |
| `oficio` | texto | `remodelações`, `eletricista` | Serviço pedido. |
| `pergunta` | texto | | Pergunta exacta, tal como foi escrita. |
| `resumo_ia_presente` | 1/0/vazio | | Se o Google mostrou o Resumo de IA. Fica vazio nos outros motores. |
| `mapa_presente` | 1/0/vazio | | Se o Google mostrou o mapa local. Fica vazio nos outros motores. |
| `plataformas_recomendadas` | texto | separadas por `\|` | Plataformas de orçamentos que a resposta mandou consultar (ex.: `Zaask\|Fixando`). |
| `corrida` | inteiro | 1–30 | N.º da pergunta na ordem da recolha. |
| `tipo` | texto | `recomendacao`, `mapa_top3` | Tipo de linha (ver acima). |
| `posicao` | inteiro | 1, 2, 3… | Ordem da empresa na resposta ou no mapa. |
| `empresa_id` | texto | `E001`… | Código anónimo da empresa. A mesma empresa tem o mesmo código em todas as linhas da edição. |
| `fonte_tipo` | texto | ver abaixo | De onde veio a recomendação. Vazio nas linhas `mapa_top3`. |
| `pagina_servico_cidade` | 1/0/`nd`/vazio | | A página citada fala daquele serviço naquela cidade (1) ou não (0). `nd` quando a fonte não é uma página web (ex.: ficha de mapa) ou não foi possível identificar a página. Vazio nas linhas `mapa_top3`. |
| `fonte_inferida` | 1/0/vazio | | 1 quando o ChatGPT não indicou a fonte, mas a nota, o n.º de avaliações e a morada eram iguais aos do mapa do Google na mesma pergunta. |
| `nota` | decimal | 1.0–5.0 ou vazio | Nota da empresa, quando a IA ou o mapa a mostraram. |
| `avaliacoes_banda` | texto | `1-9`, `10-49`, `50-199`, `200+`, vazio | N.º de avaliações em bandas. O número exacto não é publicado. |
| `nota_origem` | texto | ver abaixo | De onde veio a nota. |

### `fonte_tipo`

| Valor | Significado |
|---|---|
| `pagina_servico_cidade` | Página do site da empresa sobre aquele serviço naquela cidade. |
| `site_proprio` | Outra página do site da empresa. |
| `ficha_google` | Perfil da Empresa no Google. |
| `dados_mapa_sem_fonte` | Cartão com nota e morada, sem fonte indicada. |
| `diretorio` | Plataforma de orçamentos (Zaask, Fixando, Habitissimo, CustoJusto). |
| `listicle` | Artigo do tipo «as melhores empresas». |

### `nota_origem`

`google_maps_top3`, `google`, `google_citada_no_resumo`, `google_inferida_igual_mapa`, `chatgpt_sem_fonte`, `chatgpt_igual_mapa_google`, `habitissimo`, `zaask`. Vazio quando não houve nota.

## `barometro-01-2026-10-29-resumo-cidades.json`

Totais por cidade → ofício → motor:
- `n`: n.º de recomendações;
- `fontes`: contagem por `fonte_tipo`;
- `ai_overview`: se o Google mostrou o Resumo de IA;
- `plataformas`: n.º de plataformas que a resposta mandou consultar.

Por cidade e ofício há também:
- `empresas_distintas`: empresas diferentes;
- `em_2_motores`: empresas recomendadas por dois motores.

## Contagens que convém saber

- **Empresas distintas:** o relatório diz 86, que é a soma por cidade e ofício. O CSV tem 85 códigos `empresa_id` nas linhas `recomendacao`, porque uma empresa de Aveiro foi recomendada nos dois ofícios.
- **Recomendações:** 94 = Google 37 + ChatGPT 35 + Perplexity 22.

## O que não está nos dados, de propósito

- **Nomes de empresas, domínios, URLs das fontes, moradas e telefones.** Muitas empresas são empresários em nome individual, e o nome é um dado pessoal.
- **O texto das respostas das IAs.** Só se publica a classificação de cada resposta.
- **A anatomia de cada empresa** (site, dados estruturados, WhatsApp). Pode sair mais tarde, só em totais por grupo.

## Ficheiros previstos (não publicados ainda)

- **`edicao-01/estabilidade-2026-10-30-31.csv`:** repetição das 30 perguntas a 30 e 31/10, com o mesmo esquema. Mede se cada IA repete as empresas de um dia para o outro. Só sai depois de estar no relatório do site.
- **`edicao-02/`:** 18 capitais de distrito e 6 ofícios, recolha de 23 a 27/11/2026. O esquema pode ganhar colunas (por exemplo `lingua_pergunta` e `intencao`). Qualquer coluna nova fica descrita aqui antes da release.
