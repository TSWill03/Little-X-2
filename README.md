# Little X 2.0 — Assistente pessoal com memória e controle

**Projeto acadêmico e de desenvolvimento de software • Ciência da Computação • IF Goiano, Campus Morrinhos**

A Little X 2.0 investiga uma forma de tornar assistentes pessoais de inteligência artificial mais fáceis de usar, com memória persistente, escolha explícita de modelos, ferramentas supervisionadas, recuperação de contexto, aprovação e auditoria.

> **Este é o futuro repositório público de apresentação.** O núcleo técnico (CORE) está em um repositório separado e privado. A separação protege o histórico de desenvolvimento e os dados operacionais.

## Testar a MeuX

**Demonstração interativa em preparação.**

O botão **Testar a MeuX** será disponibilizado aqui **somente após** a validação de um ambiente isolado no site do projeto. Não existe link público funcional de teste neste momento.

Na demonstração pretendemos permitir conversa com IA real, escolha de cidade e aparência da interface, personalização de preferências e organização de listas/tarefas. O uso ocorrerá em sessão de visitante isolada, sem acesso aos arquivos, ferramentas administrativas, memórias ou credenciais do autor.

## Como o protótipo funciona

```text
Interface Web / CLI
        |
        v
  AgentRuntime (Python / FastAPI)
        |
        +-- ProviderRouter -> modelos locais ou remotos, conforme configuração
        +-- Memória e sessões -> SQLite
        +-- Tool Registry -> Policy Engine -> aprovações e auditoria
        +-- Fallback explícito (static_only não é resposta gerada por LLM)
```

## Estado e limites da pesquisa

**Elementos implementados e documentados no CORE:** runtime FastAPI, SQLite, sessões, memória textual, roteamento de modelos, fallback, ferramentas supervisionadas, política de permissões, aprovações, auditoria e interface Web. A evolução de modos simples/avançados, histórico e projetos está em branches de desenvolvimento, e não deve ser confundida com o estado de produção.

**Evidência histórica datada:** o material acadêmico de 03/11/2026 informa 175 testes automatizados aprovados na revisão de desenvolvimento então avaliada. Esse resultado **não foi reexecutado** durante a preparação desta vitrine.

**Ainda não comprovado como produto:** instalação sem assistência por pessoas não técnicas, autenticação segura para visitantes públicos, usabilidade universal, integração com WhatsApp, navegação autônoma no portal acadêmico e monitoramento periódico de localização. Esses recursos pertencem à pesquisa e ao roadmap.

A Little X 2.0 **não é um modelo de linguagem treinado do zero**. É uma arquitetura para operar e supervisionar modelos existentes de forma controlada.

## Privacidade e apresentação

Antes da abertura pública, a experiência de visitante precisará ser testada quanto à separação de sessões, retenção de dados, limites de uso, acesso HTTPS e consentimento. **Não forneça senhas, tokens, dados bancários, dados acadêmicos pessoais ou informações sensíveis na demonstração.**

O QR do pôster de 2026 deve continuar apontando para o mesmo endereço público da vitrine após a migração. O pôster impresso não será modificado; evoluções posteriores serão marcadas como tais.

**Responsável pelo projeto:** Wícolly Pedro Alcântara • Bacharelado em Ciência da Computação • IF Goiano — Campus Morrinhos.

_Este repositório de vitrine não disponibiliza nem licencia o código privado do CORE._
