# Process log — Support Intelligence

Este arquivo é o índice das evidências de processo desta implementação. A narrativa completa, com decisões, correções, testes e limitações, está em [docs/05-validacao-demo-processo.md](../docs/05-validacao-demo-processo.md).

## Ferramentas e uso

- **Codex:** leitura dos briefs, decomposição, implementação, execução de testes e revisão final.
- **Ponytail:** escolha da menor solução correta; reutilização do pipeline, SQLite, polling e componentes já existentes.
- **Agentes de revalidação:** auditorias independentes de dados, design, contratos, specs e release.
- **Python e scripts locais:** auditoria dos CSVs, preparação de artefatos, treino, embeddings, FAISS e testes de API.
- **Navegador local:** smoke tests das seis lentes, da rota O Início, dos deep links e da persistência do Ticket Lab.

## Como o trabalho foi decomposto

1. Ler integralmente os READMEs, `CONTRIBUTING.md` e `submission-guide.md`.
2. Auditar os dois datasets e congelar as limitações antes de prometer métricas.
3. Especificar arquitetura, sprints, contratos e cada lente com checkboxes.
4. Implementar o núcleo compartilhado e validar backend, frontend e integração.
5. Exercitar as rotas no navegador e corrigir contexto, origem, acessibilidade textual e nomenclatura.
6. Adicionar O Início com a narrativa Hermes → Codex → planejamento e a camada neon interativa do Graph sem alterar scores ou evidências.
7. Reler todas as specs, manter pendências abertas e executar a bateria final.

## Erros encontrados e correções

- Os timestamps do Dataset 1 pareciam permitir TTR/FRT, mas não havia abertura válida; o produto passou a exibir indisponibilidade.
- O overview do Graph não tinha relações agregadas; foram calculados centroides dos embeddings reais, com método e score expostos.
- Filtros de CSAT previstos na spec não estavam na UI; foram adicionados com testes de presença e nota.
- O resultado do Ticket Lab não persistia no endereço da página; o deep link agora inclui a identidade e restaura o resultado após recarga.
- O replay chamava um contador de política de “triagem automática” e tratava um ordinal como “segundos”; a API agora chama a janela de `window_steps` e as legendas evitam interpretação operacional indevida.
- O primeiro rascunho do Graph só destacava arestas; a revisão acrescentou nós neon pequenos, seleção que isola a vizinhança, segundo clique/fundo para restaurar, arraste individual e transição do workspace.
- O onboarding tinha um checklist visual que não produzia evidência; ele foi removido e substituído por uma narrativa em primeira pessoa e um card com o comando local reproduzível.
- Smoke test final: O Início mostrou a narrativa e o comando; Graph mostrou 28 nós neon e o isolamento/restauração de uma seleção, sem warnings/erros do navegador.

## O que depende de validação humana

Relevância de vizinhos, clusters, duplicatas e resoluções; benchmark em português/DS1; autenticação, rate limiting, monitoramento e ensaios formais de teclado, 320 px, zoom, reduced motion, reconexão e duas abas continuam marcados nas specs.

## Evidências reproduzíveis

```sh
pnpm --dir frontend run check
pnpm --dir frontend test
pnpm --dir frontend run build
.venv/bin/python tests/test_data_pipeline.py
.venv/bin/python tests/test_backend.py
SUPPORT_BASE_URL=http://127.0.0.1:8000 .venv/bin/python tests/test_integration.py
```

O histórico Git deste diretório complementa a narrativa. Nenhum CSV original, resolução ou resposta foi alterado; o Copilot registra feedback local e não envia mensagens externas.
