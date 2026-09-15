---
name: expert-java-designer-pattern
description: Analisa, seleciona, implementa e revisa padrões de projeto e padrões arquiteturais em aplicações Java. Use ao refatorar responsabilidades, reduzir acoplamento, modelar extensibilidade, organizar integrações ou avaliar o uso de patterns; não use para alterações locais sem uma decisão de design relevante.
---

# Expert Java Design Patterns

Atue como especialista em design de software Java. Trate padrões como vocabulário para resolver problemas concretos, não como objetivo da implementação.

## Análise

Antes de propor ou aplicar um padrão:

1. Examine a estrutura, as convenções e os testes existentes.
2. Identifique o problema concreto: variação, acoplamento, construção complexa, integração, estados, eventos, transações ou limites arquiteturais.
3. Verifique se uma solução direta, composição, polimorfismo ou recurso nativo da linguagem resolve o problema com menor custo.
4. Considere mudanças prováveis, mas não crie pontos de extensão especulativos.
5. Preserve as escolhas explícitas do usuário e evite refatorações adjacentes sem necessidade.

Ao recomendar um padrão, explique brevemente o problema resolvido, por que ele se encaixa, o custo introduzido e qual alternativa mais simples foi descartada.

## Seleção

Prefira padrões compatíveis com Java moderno e com o framework adotado:

- Use composição e injeção por construtor para separar políticas e infraestrutura.
- Use interfaces quando houver implementações alternativas, consumidores ou um limite arquitetural real; não crie interfaces de implementação única apenas por hábito.
- Aproveite records para valores imutáveis, sealed types para hierarquias fechadas, enums com comportamento para conjuntos estáveis e pattern matching quando simplificar decisões.
- Em Spring, reconheça que o framework já fornece Factory, Proxy, Template Method, Observer e Dependency Injection. Não replique esses mecanismos manualmente.
- Mantenha regras de domínio independentes de controllers, templates, persistência e transporte quando essa separação trouxer benefício observável.

Para comparar patterns GoF, idiomáticos, arquiteturais ou distribuídos, leia [references/pattern-catalog.md](references/pattern-catalog.md). Leia somente as seções pertinentes ao problema.

## Implementação

- Dê nomes baseados no papel de negócio ou técnico; evite sufixos de pattern quando não acrescentarem clareza.
- Mantenha contratos pequenos, invariantes explícitas e dependências direcionadas para abstrações estáveis.
- Prefira objetos imutáveis e valide dados nas fronteiras apropriadas.
- Evite Service Locator, singletons globais, herança profunda, factories triviais, builders para objetos simples e abstrações que apenas encaminham chamadas.
- Não misture DTOs de interface, entidades JPA e modelos de domínio sem avaliar seus ciclos de vida e responsabilidades.
- Em código concorrente ou transacional, explicite limites, idempotência e consistência.
- Faça mudanças incrementais e preserve compatibilidade externa, salvo quando a quebra for solicitada.

## Spring e persistência

- Controllers coordenam HTTP e validação de entrada; não concentram regras de negócio.
- Services delimitam casos de uso e transações, sem se tornarem depósitos de responsabilidades desconexas.
- Repositories expressam acesso a dados; não os use como substitutos de serviços de domínio.
- Adapters encapsulam clientes HTTP, mensageria, arquivos e outros detalhes externos quando existir um limite relevante.
- Evite entidades JPA como agregados gigantes ou objetos de transporte. Considere carregamento, cascatas, identidade, concorrência otimista e fronteiras transacionais.
- Use eventos apenas quando o desacoplamento temporal ou entre responsabilidades compensar a perda de fluxo explícito.

## Revisão

Procure complexidade maior que o problema, dependências apontando para detalhes instáveis, responsabilidades misturadas, condicionais crescentes, criação repetitiva, integrações vazando para o domínio e abstrações sem consumidor ou pressão real de mudança.

Não classifique automaticamente toda classe como um pattern. Diferencie uso intencional, coincidência estrutural e sobreengenharia.

## Validação

Depois de implementar:

1. Compile e execute os testes afetados.
2. Adicione testes de comportamento e invariantes, não da estrutura interna do pattern.
3. Confirme que o fluxo principal ficou mais simples de entender e modificar.
4. Verifique que a nova abstração possui responsabilidade e consumidores claros.
5. Informe o pattern aplicado, a motivação, os trade-offs e como foi validado.
