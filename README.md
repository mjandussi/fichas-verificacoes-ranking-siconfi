# Fichas das verificações do Ranking Siconfi

Fichas de operacionalização e análise das **72 verificações de consistência no cruzamento de dados** (17 da D2, 28 da D3 e 27 da D4) do Ranking da Qualidade da Informação Contábil e Fiscal no Siconfi, exercício de 2025, aplicadas aos 92 municípios do Estado do Rio de Janeiro.

Este repositório é parte do Produto Técnico-Tecnológico (PTT) da dissertação de mestrado profissional de Marcelo Jandussi Walther de Almeida, no Programa de Pós-Graduação em Controladoria e Gestão Pública da Universidade do Estado do Rio de Janeiro (PPGCGP/UERJ), cujo tema é a operacionalização e a análise sistemáticas e rastreáveis das verificações do Ranking.

> **Situação: em revisão (20/10/2026).** As 72 fichas estão completas e passaram pelo verificador automático de estrutura e de citações, mas a revisão do autor é por amostragem e ainda está em curso. Cada ficha traz seu próprio aviso de situação.

## Para que servem

A STN publica, para cada verificação do Ranking, uma descrição curta. Executá-la exige decisões que a descrição não registra: quais contas e anexos entram, qual coluna ou período se lê, como tratar ausências, sinais e tolerâncias. A ficha registra essas decisões para uma verificação, de modo que possam ser lidas, contestadas e refeitas por outra pessoa. Ela pode apoiar a montagem de uma análise em qualquer período.

## Conteúdo

| Pasta | O que há |
|---|---|
| `fichas/` | 72 fichas, uma por verificação (`Ficha_D2_00044.md` etc.) |
| `dados/` | Resultados e comparações de três rodadas de aplicação |

### Como ler uma ficha

Cada ficha tem dez seções, que acompanham as etapas do método:

1. **Identificação**: código, dimensão, combinação de fontes, versão da ficha.
2. **Descrição oficial**: transcrição literal da página de metodologia do Ranking (cópia de 17/09/2026).
3. **Interpretação**: o que a descrição não diz e a leitura adotada.
4. **Aplicabilidade e comparabilidade**: a quem se aplica e quando o resultado é comparável.
5. **Dados e parâmetros**.
6. **Tratamentos**: ausências, sinais, tolerâncias.
7. **Condição lógica** da regra, como implementada.
8. **Execução e evidências**: exemplo de execução com valores.
9. **Confronto com o Ranking Diário**: resultado nas rodadas.
10. **Investigação e refinamento**: histórico de versões, hipóteses testadas e decisão. Fichas de regras refinadas estão na versão 2.

### Duas leituras que a ficha distingue

- **OK/ERRO** (ou ACERTO/ERRO) descrevem o resultado da regra para o município.
- **CONVERGENTE/DIVERGENTE/NÃO COMPARÁVEL** descrevem o confronto desse resultado com a nota que a STN divulga no Ranking Diário.

## Dados

As pastas de `dados/` contêm, para cada rodada, três arquivos de resultado:

- `comparacoes.csv`: um registro por par município-verificação, com o resultado da regra, a nota do Ranking Diário e o status do confronto;
- `divergencias.csv`: os pares divergentes;
- `resumo_regras.csv`: totais, pares comparáveis, convergentes e aderência por verificação.

As rodadas de consolidação e de confirmação trazem ainda o `manifesto.json` (data da execução, commit do código, códigos de integridade dos módulos das fórmulas, hashes dos arquivos do Ranking Diário e versões dos programas) e o `SHA256SUMS.txt` (códigos de integridade dos arquivos do pacote da rodada; parte desses arquivos, como os detalhes por município, não está neste repositório). Esses arquivos não contêm código.

| Rodada | Pasta | Observação |
|---|---|---|
| Desenvolvimento, agosto/2026 | `rodada-1-desenvolvimento-2026-08` | Execução final do ciclo de agosto, com 37 municípios (bloco inicial) |
| Consolidação, 19/09/2026 | `rodada-3-consolidacao-2026-09-19` | 86 municípios avaliados dos 92; regras após os refinamentos de setembro |
| Confirmação, 02/10/2026 | `rodada-4-confirmacao-2026-10-02` | 86 municípios avaliados dos 92; regras congeladas em 20/09/2026 |

A rodada de setembro (04/09/2026) e as fontes brutas preservadas não estão neste repositório.

## Limites e cuidados

- **Convergência com a STN não é validação universal.** O Ranking Diário é a referência operacional para o confronto, não um gabarito. Divergência abre investigação, não ajuste automático.
- **As rodadas de desenvolvimento não são teste independente**: os casos que revelaram problemas serviram para corrigir as regras. A rodada de confirmação é o teste independente disponível, restrito aos mesmos municípios e a uma única fotografia.
- **Escopo.** As conclusões valem para estas 72 verificações em 2025 e para os municípios fluminenses. Zero em outro exercício pode significar regra não vigente.
- **Ausência de demonstrativo obrigatório não equivale a valor zero.** Quando não há dados, o resultado é não comparável ou falha de cobertura, conforme o caso.
- **Uma não pontuação não é, por si, erro material.**

### Os marcadores `[VERIFICAR]`

Aparecem em todas as fichas e registram o que não pôde ser comprovado. Os mais frequentes: (a) o código anterior ao primeiro commit versionado (29/08/2026) não tem histórico, de modo que a versão original de algumas regras não pôde ser conferida por commit; (b) commits de refinamento citados nos registros de decisão não existem no histórico local do repositório de trabalho; (c) valores de execuções que não têm pacote preservado. Os caminhos de arquivo e os identificadores de commit citados nas fichas pertencem ao repositório de trabalho do autor, que não é público.

## Sobre o código

A implementação computacional (Python) que executou as regras não é divulgada. As fichas descrevem cada regra com o detalhe necessário para reimplementá-la: fontes, parâmetros, tratamentos e condição lógica. A *especificação* das regras pode ser examinada a partir deste repositório; a conferência da procedência das rodadas (commit, tag e códigos de integridade dos módulos) e a *reexecução* dependem do acesso ao código, restrito ao autor.

## Como citar

ALMEIDA, Marcelo Jandussi Walther de. *Fichas das verificações do Ranking Siconfi* (Produto Técnico-Tecnológico). Rio de Janeiro: PPGCGP/UERJ, 2026. Disponível em: https://github.com/mjandussi/fichas-verificacoes-ranking-siconfi. A referência completa da dissertação será acrescentada após o depósito.

## Licença

MIT (ver `LICENSE`).

## Aviso

Este material não é oficial e não substitui a metodologia da Secretaria do Tesouro Nacional, a quem pertence o Ranking. A homologação e a eventual retificação das informações cabem a cada ente, e o julgamento profissional permanece necessário.
