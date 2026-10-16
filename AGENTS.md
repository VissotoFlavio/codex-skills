# Orientações para agentes de IA

## Objetivo do repositório

Este repositório cataloga skills públicas e reutilizáveis para o Codex. Trate cada diretório em `skills/` como uma unidade independente e mantenha as mudanças limitadas à skill solicitada.

## Antes de alterar uma skill

1. Leia o `README.md` raiz, o `SKILL.md` da skill e os documentos em `references/`, quando existirem.
2. Preserve a estrutura e os nomes de arquivos esperados pela plataforma.
3. Confirme que não há segredos, credenciais, dados pessoais, URLs privadas ou caminhos específicos da máquina nos arquivos.

## Ao criar ou atualizar skills

- Mantenha o `SKILL.md` conciso, operacional e com escopo claro.
- Documente no `README.md` da skill: propósito, quando usar, quando não usar, exemplos de prompts, pré-requisitos e limitações.
- Inclua referências somente quando forem necessárias para execução correta.
- Evite instruções destrutivas, automações externas sem autorização e dependências não documentadas.
- Preserve atribuições e licenças aplicáveis a conteúdo importado.

## Validação

- Verifique links relativos e caminhos citados pela skill.
- Inspecione o diff para garantir que a alteração pertence ao escopo solicitado.
- Não adicione arquivos gerados, tokens, logs ou configurações locais.

## Git e GitHub

- Use `gh` exclusivamente para operações com GitHub e execute `gh auth status` antes delas.
- Use commits no formato Conventional Commits.
- Não faça commit diretamente em branches protegidas; siga a política de branches do repositório de destino ao aplicar uma skill.
