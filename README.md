# Little X 2.0 — Uma assistente pessoal de IA com memória, modelos e controle

**Pesquisa e desenvolvimento em Ciência da Computação • IF Goiano, Campus Morrinhos**
**Projeto em demonstração experimental de portas abertas • Novembro de 2026**

A **Little X 2.0** pesquisa como tornar assistentes pessoais de inteligência artificial mais simples de usar, mantendo transparência, memória persistente, roteamento de modelos locais/remotos e controle de ações. Não estamos treinando um novo modelo de linguagem do zero: construímos um **runtime** que coordena modelos existentes e ferramentas supervisionadas.

## Experimente a MeuX

### [**Abrir a demonstração interativa →**](https://wicolly.com.br/meux/)

**[https://wicolly.com.br/meux/](https://wicolly.com.br/meux/)**

Esta é a versão pública **de laboratório da interface MeuX**. Você pode entrar sem conta e experimentar, em um único chat, comandos básicos como consultar o horário, criar uma lista de compras, salvar compromissos **somente neste navegador** (com confirmação) e pesquisar artigos científicos via Crossref.

**Limite importante:** o site público ainda **não** está conectado ao modelo LLM, ao CORE privado nem ao WhatsApp. Ele não envia mensagens nem notificações, não coleta número de telefone e não consegue interpretar áudios/imagens por IA. Por isso, as respostas dessa página sobre ações locais não equivalem a uma conversa com modelo de linguagem. O protótipo mais avançado segue em desenvolvimento e homologação; não há botão falso de envio.

Se você veio pelo **QR Code do pôster**, a experiência planejada é: **QR → este GitHub → Testar a MeuX → https://wicolly.com.br/meux/**. A URL do QR físico ainda deve ser confirmada por leitura no celular. O banner impresso não será alterado.

## Como funciona o CORE privado

```text
Interface Web / CLI / canais supervisionados
                 |
                 v
          AgentRuntime (Python)
                 |
     +-----------+-------------+
     |                         |
 ProviderRouter         Tool Registry
     |                         |
 Ollama / NVIDIA NIM       Policy Engine
     |                         |
 Fallback explícito         Aprovações
                 |
          SQLite / Auditoria
```

**Componentes documentados:** FastAPI, SQLite e migrations, sessões, memória textual, seleção de modelos, fallback, ferramentas supervisionadas, políticas de risco, solicitações de aprovação e registros de auditoria. A versão executada no Hefesto não deve ser confundida com funcionalidades que ainda estão em branches de desenvolvimento.

**Pesquisa e evidência:** o material acadêmico de 03/11/2026 reportou 175 testes automatizados aprovados em uma revisão de desenvolvimento; esse número é histórico, não um resultado reexecutado em produção nesta página. Não há avaliação formal de usabilidade universal nem demonstração de segurança multiusuário.

## Por que a demonstração é limitada?

O protótipo completo busca permitir lembretes e listas via WhatsApp, pesquisa, leitura de anexos e roteamento local/cloud, preservando autorização e privacidade. Antes da abertura a visitantes, precisamos verificar o vínculo do número WhatsApp, a segurança de uploads, isolamento de sessões, limites de requisição e capacidade real sob carga. **400 participantes esperados não significam 400 conversas simultâneas validadas.**

A versão pública permite conhecer a interface e fornecer feedback sem expor servidores, terminal, credenciais, bancos ou ferramentas administrativas.

## Código, versões e continuidade

- **Site público da demonstração:** [Wicolly-Sites](https://github.com/TSWill03/Wicolly-Sites/tree/main/meux), com implementação do laboratório estático.
- **CORE privado:** `TSWill03/Little-X-2-Core`, separado por segurança.
- **Histórico preservado:** quatro versões ZIP (v1, v2, v3 e v4) commitadas em sequência na branch privada `feat/meux-demo-versioned-20261109`. São **snapshots experimentais**, não releases estáveis.

## Privacidade e feedback

Não forneça senhas, documentos pessoais, dados bancários nem arquivos sensíveis. Listas e compromissos desta página ficam somente no navegador; após 45 minutos sem interação, os dados são considerados expirados e descartados na próxima visita/atividade. Pesquisas consultam o serviço externo Crossref. Para pedir melhorias, utilize o repositório público ou entre em contato pelos canais confirmados do autor.

**Autor:** Wícolly Pedro Alcântara · Bacharelado em Ciência da Computação · IF Goiano — Campus Morrinhos.

_Este repositório é uma vitrine pública independente e não disponibiliza nem licencia o código privado do CORE._
