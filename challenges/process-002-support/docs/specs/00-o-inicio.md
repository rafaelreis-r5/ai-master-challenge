# Spec 00 — O Início

**Rota:** `/#/inicio`
**Papel:** onboarding da demonstração; não é uma sétima lente analítica.

## Objetivo

Dar a um gestor, avaliador ou agente sem conhecimento técnico um ponto de partida único. A tela explica os dois datasets, o significado dos estados, a ordem da demonstração e os limites que precisam ser ditos em voz alta. Ela não calcula métricas novas nem cria uma sessão.

## Conteúdo e ações

| Bloco | O que a pessoa entende/faz |
|---|---|
| Status do corpus | Confere que o catálogo carregou e vê as contagens verificadas de DS1 e DS2. |
| Antes de apresentar | Aprende que DS1 contém operação/CSAT/resoluções e DS2 contém texto/categorias de TI; o seletor Corpus fica no topo. |
| Caminho recomendado | Percorre oito passos: corpus → diagnóstico → estratégia → ticket novo → Copilot → Graph → replay → limites. |
| Seis lentes | Abre cada rota com dataset e origem compatíveis, preservando o contexto global. |
| Como ler um resultado | Diferencia histórico, simulação, entrada manual, confiança, revisão humana e indisponibilidade. |
| Checklist da entrevista | Marca localmente os pontos que já foram explicados durante a apresentação. |

Os botões **Começar pelo diagnóstico** e **Testar um ticket** são atalhos; os cartões das seis lentes repetem os destinos com uma explicação curta. A seleção do checklist é apenas visual e não é registrada como evidência de negócio.

## Limites comunicados

- A ordem e os horários do Live Replay são simulados, embora o texto venha dos arquivos.
- FRT/TTR permanecem indisponíveis porque falta uma data de abertura válida.
- O Graph é uma rede semântica de embeddings, não uma visualização dos neurônios do classificador.
- Confiança, similaridade, cluster e posição 2D são medidas diferentes.
- A demonstração não envia mensagens, fecha tickets, altera CSVs ou substitui revisão humana.

## Checkpoints

- [x] `INI-01`: rota carregada pelo shell, com dataset e sessão preservados na navegação.
- [x] `INI-02`: roteiro explica as seis lentes e a distinção entre dados observados, hipóteses e simulação.
- [x] `INI-03`: contagens vêm do catálogo compartilhado e ausência de catálogo não é tratada como métrica zero.
- [x] `INI-04`: links abrem destinos reais por teclado e o conteúdo não depende do Graph.
- [ ] `INI-05`: ensaio dedicado em 320 CSS px, zoom 200% e leitor de tela.
