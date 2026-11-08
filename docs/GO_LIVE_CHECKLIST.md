# Preparação da virada da URL do pôster — checklist operacional

**Situação:** preparação. Ainda NÃO renomear o CORE e NÃO tornar pública a vitrine até satisfazer os gates.

## G0. Integridade e dependências

- [ ] Confirmar com leitura do QR físico que o destino é exatamente `https://github.com/TSWill03/Little-X-2`.
- [x] Confirmar `TSWill03/Little-X-2` como privado (GitHub; revisão em 07/11/2026).
- [x] Identificar branch principal `main`, branches de novembro e PR #1.
- [x] Identificar que Hefesto `/srv/littlex` usa `git@github.com:TSWill03/Little-X-2.git` (checkout limpo observado em 07/11/2026).
- [ ] Inventariar e proteger remotes de **todos** os clones, principalmente os dois worktrees do Destruking descritos no dossiê, antes de reutilizar o nome público.
- [ ] Verificar outros clones, integrações, automações GitHub, webhooks, actions, deploy keys e README/documentos com links antigos.
- [ ] Validar se dados pessoais/segredos aparecem no histórico e **não transportar histórico do CORE** para a vitrine pública.

## G1. Backup e rollback

- [x] Backup espelho Git do CORE com `gh repo clone -- --mirror` em `/home/ubuntu/littlex-migration-20261107/Little-X-2-pre-rename.git`, no Hefesto; `git fsck` executado.
- [x] Bundle Git de `1.6 MiB` e checksum SHA-256 no mesmo diretório, com `git bundle verify` (07/11/2026).
- [ ] Exportar inventário de PRs/issues, configurações, branch protections, labels, webhooks e deploy keys de modo sanitizado.
- [ ] Preparar plano de rollback **testado** para eventual falha de rename/recriação; não confiar exclusivamente no redirect do GitHub.
- [ ] Atualizar o `origin` do Hefesto e dos worktrees Windows para o **novo endereço privado** antes de reservar o nome antigo para a vitrine pública. Preservar working trees e alterações não commitadas.

## G2. Sequência de migração (somente após G0 e G1)

1. Pausar operações Git automatizadas do projeto temporariamente (sem interromper o runtime de produção).
2. Revalidar `git status`, HEAD, branch, remotes e backup. Não executar `reset --hard`, `clean`, `pull --rebase` nem migrations.
3. Renomear repositório **existente e privado** `TSWill03/Little-X-2` para `TSWill03/Little-X-2-Core` (ou outro nome validado como livre), mantendo o mesmo ID, PRs e histórico.
4. Atualizar e verificar `origin` nos clones que precisam continuar enviando código ao CORE (Hefesto, Destruking, demais dispositivos). Evitar antigos remotes gravando no novo repositório público.
5. Renomear `TSWill03/Little-X-2-Showcase-Staging` para **`TSWill03/Little-X-2`** somente após assegurar que a URL anterior não é utilizada por clients de push.
6. Auditar vitrine: somente arquivos sanitizados, sem histórico privado, sem secrets, sem credenciais e sem código privado.
7. Tornar a **vitrine** pública e testar HTTP em navegador anônimo e celular. CORE permanece privado.
8. Testar links de documentação; ajustar índices do Notion e site. Sem alteração do pôster impresso.

## G3. Botão de demonstração

- [ ] Site do usuário disponibiliza uma rota real de demonstração MeuX por HTTPS.
- [ ] API convidado tem autenticação/sessão segregada, limite de requisições e auditoria apropriada.
- [ ] Chat com LLM real e `effective_provider` verificado, com `static_only` claramente identificado.
- [ ] Sem acesso a SQLite, arquivos, tokens, ferramentas e memória do proprietário.
- [ ] Dois visitantes independentes testados, além de reinício/queda de rede.
- [ ] Somente após isso: atualizar botão **Testar a MeuX** no README público com URL efetivamente testada.

## Avisos críticos

A documentação do GitHub alerta que ao reutilizar o nome antigo de um repositório renomeado, **os redirects deixam de funcionar**. Isso inclui possíveis operações de clone, fetch e push pelo endereço antigo, que passam a resolver o repositório novo. Verificar especialmente remotes dos worktrees Windows off-line antes de disponibilizar a vitrine.

Referências:
- [Renaming a repository — GitHub Docs](https://docs.github.com/en/repositories/creating-and-managing-repositories/renaming-a-repository)
- [Projeto privado atual](https://github.com/TSWill03/Little-X-2)
- [PR draft de escopo da demo](https://github.com/TSWill03/Little-X-2/pull/1)

**Nenhuma etapa G2 foi autorizada a prosseguir automaticamente se os gates anteriores falharem.**
