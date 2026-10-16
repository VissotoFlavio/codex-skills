# Codex Skills

Repositório público para reunir skills reutilizáveis no Codex. Cada skill fica isolada em `skills/<nome-da-skill>` e inclui sua definição, referências e um guia prático de uso.

## Skills disponíveis

| Skill | Descrição |
| --- | --- |
| [issue-to-pr-review](skills/issue-to-pr-review/README.md) | Conduz uma entrega de GitHub a partir de uma issue, incluindo implementação, validação, Pull Request, análise de comentários, correções e verificação final. |

## Estrutura

```text
skills/
  issue-to-pr-review/
    SKILL.md          # definição consumida pelo Codex
    README.md         # guia de uso, exemplos e orientações
    agents/           # configuração de agentes da skill
    references/       # contratos detalhados do fluxo
AGENTS.md             # instruções para agentes que trabalham neste repositório
```

## Como usar

1. Escolha uma skill na tabela acima e leia seu `README.md`.
2. Copie ou instale a pasta completa da skill, preservando `SKILL.md`, `references/` e `agents/` quando existirem.
3. Acione a skill apenas quando a solicitação corresponder ao escopo descrito por ela.

## Contribuições

Novas skills devem ser autocontidas, documentadas e seguras para publicação. Não envie chaves, tokens, dados pessoais, caminhos locais ou instruções que ampliem permissões sem necessidade.

Este repositório é licenciado sob a [MIT License](LICENSE).

## Atribuição

A skill `issue-to-pr-review` é distribuída sob a licença MIT e foi originalmente criada no projeto [asgard-codex-skill](https://github.com/VissotoFlavio/asgard-codex-skill).
