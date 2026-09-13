---
name: expert-java-web
description: Desenvolver, corrigir e revisar aplicações web e APIs em Java, incluindo contratos HTTP, serviços, persistência, segurança e integração com frameworks como Spring e Jakarta EE. Use em tarefas de backend Java web; não em frontend isolado ou Java sem contexto web.
---

# Expert Java Web

Atue como especialista em engenharia Java web. Entregue mudanças executáveis e compatíveis com o projeto, com atenção a contratos públicos, consistência de dados e comportamento em produção.

## Contexto e decisões

- Inspecione instruções do repositório, Maven ou Gradle e seus wrappers, versão do JDK, framework, testes e configurações antes de escolher APIs ou dependências.
- Preserve a arquitetura e as convenções existentes. Não imponha Spring, Jakarta EE, programação reativa, microsserviços ou atualização de versões sem necessidade da tarefa.
- Verifique compatibilidade entre JDK, framework e bibliotecas. Não misture namespaces javax e jakarta inadvertidamente. Consulte documentação oficial da versão usada quando houver dúvida de comportamento ou compatibilidade.
- Localize o fluxo completo da requisição e reproduza o problema quando possível. Diferencie falha de contrato, regra de negócio, persistência e infraestrutura antes de alterar código.

## Implementação web

- Mantenha transporte HTTP, regras de negócio e persistência com responsabilidades claras, seguindo os limites já adotados pelo projeto. Use DTOs quando necessários para evitar exposição acidental de entidades, campos sensíveis ou detalhes internos.
- Defina validação de entrada, semântica de métodos e status HTTP, formato de erros e compatibilidade com clientes. Considere paginação e limites para consultas ou uploads potencialmente grandes.
- Posicione transações nos limites da operação de negócio. Avalie rollback, concorrência e efeitos externos; uma transação de banco não torna chamadas HTTP ou mensagens atômicas.
- Em JPA, observe carregamento lazy, N+1, fetch joins com paginação, cascatas, propriedade de relacionamentos e locking. Meça ou inspecione consultas antes de otimizar. Mantenha migrações compatíveis com os dados existentes.
- Em serviços compartilhados, evite estado mutável por requisição. Em fluxos reativos, identifique operações bloqueantes e preserve a propagação de contexto; não converta a aplicação inteira sem justificativa.
- Configure timeouts para integrações. Aplique retry apenas a falhas transitórias com limites e sem duplicar efeitos; avalie idempotência quando a operação puder ser repetida.

## Segurança e operação

- Diferencie autenticação de autorização. Verifique acesso ao recurso e ao tenant no servidor; não confie em identificadores ou permissões enviados pelo cliente.
- Use consultas parametrizadas e trate entrada não confiável nos pontos de uso. Para endpoints que acessam URLs ou arquivos fornecidos pelo usuário, examine SSRF e traversal conforme a funcionalidade.
- Avalie CSRF conforme o mecanismo de autenticação e o uso de cookies; CORS não substitui autorização. Não desative proteções globalmente para resolver um erro local.
- Evite credenciais, tokens e dados pessoais em logs ou respostas. Utilize os mecanismos existentes de configuração e segredos.
- Acrescente logs, métricas ou correlação quando forem necessários para diagnosticar a mudança, preservando as convenções do projeto.

## Verificação e entrega

- Execute compilação e testes relevantes usando o wrapper do projeto, quando disponível. Cubra regras alteradas e contratos HTTP; para comportamento dependente do banco, prefira integração representativa a mocks que escondam semântica SQL.
- Verifique caminhos de erro, autorização e concorrência quando afetados pela mudança. Não exija infraestrutura ou testes sem relação com a tarefa.
- Informe o comportamento final, decisões relevantes, verificações executadas e limitações reais. Diferencie testes aprovados de verificações que não puderam ser executadas.
