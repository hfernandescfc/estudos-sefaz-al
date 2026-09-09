# estudos-sefaz-al

Dashboard de estudos do ciclo **SEFAZ-AL / Auditor Fiscal da Administração Tributária Estadual (AFTE)** — banca CEBRASPE, objetiva em 20/12/2026, discursiva em 10/01/2027.

🔗 **https://hfernandescfc.github.io/estudos-sefaz-al/**

Sucede o [`estudos-tce`](https://github.com/hfernandescfc/estudos-tce) (TCE-PE, banca FGV), que continua no ar com os dados daquele ciclo.

## O que é

Página única, sem build e sem dependência externa: HTML/JS vanilla lendo JSON. O estado do usuário (sessões, status por tópico, revisões feitas) vive no `localStorage` e, opcionalmente, sincroniza entre máquinas por um **Gist secreto** — o token fica só no `localStorage` de cada máquina e nunca entra no repositório.

## Arquivos

| Arquivo | Origem | O que traz |
|---|---|---|
| `index.html` | mantido à mão | o dashboard inteiro (7 abas) |
| `revisoes_estado.json` | `gerar_fila.py --confirmar` | cadeias de revisão D+1/D+6/D+14/D+28 por assunto |
| `desempenho_assuntos.json` | `desempenho_assuntos.py` | desempenho por matéria e assunto |
| `execucao_tec.js` | `desempenho_assuntos.py` | progresso por tópico do cronograma |
| `sessoes_tec.js` | `gerar_sessoes_tec.py` | sessões de estudo derivadas das capturas do TEC |

Tudo abaixo da primeira linha é **derivado** — regerar pelos scripts em `06_Scripts/`, não editar à mão.

## Métrica

A banca é CEBRASPE, com **itens certo/errado e anulação**: errada anula certa. Acerto bruto não é comparável ao ciclo FGV — a linha de base do chute vai de 20% para 50%. A métrica do painel é o **saldo líquido** (`acertos − erros`, ou `2p − 1`):

| Acerto bruto | Saldo líquido |
|---|---|
| 50% | 0% — chute puro |
| 65% | 30% — piso de eliminação do edital |
| 80% | 60% — meta do plano |
| 85% | 70% — limiar de domínio |

O `index.html` detecta o formato pelo campo `formato` do JSON: arquivo do ciclo antigo, sem os campos, cai automaticamente no acerto bruto.
