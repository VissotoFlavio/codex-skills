# issue-to-pr-review

Skill para conduzir, com rastreabilidade, o ciclo de uma issue até a revisão de um Pull Request. Ela cobre implementação, validação, análise de feedback, correções e verificação final, sempre respeitando o nível de autorização disponível.

## Quando usar

Use esta skill quando houver uma issue de GitHub que precise ser entregue ou quando for necessário tratar a revisão de um Pull Request já existente.

Os modos disponíveis são:

| Modo | Uso |
| --- | --- |
| `DELIVER` | Implementar o escopo aprovado de uma issue, validar e abrir um Pull Request quando autorizado. |
| `REVIEW_COMMENTS` | Ler e classificar comentários de revisão, sem alterar o código. |
| `CORRECT` | Corrigir comentários de revisão explicitamente autorizados e atualizar o Pull Request. |
| `VERIFY` | Verificar se correções resolvem os achados sem introduzir regressões, sem alterar arquivos. |

## Modelos de uso

### Entrega de uma issue

```text
Use a skill issue-to-pr-review no modo DELIVER para a issue #123.
Implemente apenas o escopo aprovado, execute as validações relevantes,
inspecione o diff e abra um Pull Request para develop.
```

### Leitura de comentários de Pull Request

```text
Use issue-to-pr-review no modo REVIEW_COMMENTS para o Pull Request #45.
Classifique cada comentário como acionável, ambíguo, obsoleto, já resolvido
ou fora de escopo. Não altere o código.
```

### Correção autorizada

```text
Use issue-to-pr-review no modo CORRECT para corrigir os comentários acionáveis
do Pull Request #45. Faça somente as correções autorizadas, execute as
validações afetadas e atualize a descrição do Pull Request.
```

### Verificação final

```text
Use issue-to-pr-review no modo VERIFY no Pull Request #45.
Mapeie cada correção ao comentário original e valide os comportamentos e
contratos afetados. Não faça alterações.
```

## Orientações de execução

- Leia as instruções do repositório antes de agir e escolha o modo mais restrito que atende ao pedido.
- Use somente `gh` para GitHub e valide a sessão com `gh auth status` antes de qualquer operação.
- Antes de criar uma branch de trabalho, confirme a branch-base, atualize-a a partir do remoto e inicie a atividade somente com essa base sincronizada.
- Após validar que uma correção atende ao comentário específico de revisão, marque a respectiva thread do GitHub como resolvida; mantenha-a aberta se a evidência for insuficiente.
- Não infira autorização para abrir PRs, fazer merge, deploy, migrations, mudanças de infraestrutura ou ações destrutivas.
- Respeite políticas de issue, branch, changelog e commits do repositório alvo.
- Use `Closes #<issue>` em Pull Requests elegíveis e envie descrições em Markdown com quebras de linha reais.
- Registre evidências: modo escolhido, autoridade disponível, issue/PR, arquivos alterados, validações, riscos e bloqueios.

## Arquivos da skill

- `SKILL.md`: instruções principais consumidas pelo agente.
- `references/delivery.md`: contrato detalhado para entrega.
- `references/review-comments.md`: regras para classificar e corrigir feedback de revisão.
- `references/verification.md`: contrato de verificação final.
- `agents/openai.yaml`: configuração complementar de agente.

## Limites

Esta skill não substitui as regras de governança do repositório nem autoriza automaticamente a próxima fase do fluxo. Por exemplo, terminar uma entrega não autoriza merge ou deploy.

## Origem

Esta skill vem do projeto [asgard-codex-skill](https://github.com/VissotoFlavio/asgard-codex-skill), de Flavio Vissoto, e é disponibilizada sob licença MIT.
