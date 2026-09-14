---
name: expert-java-designer-patterns
description: Selecionar, implementar, explicar e revisar design patterns em Java, incluindo padrões GoF e refatorações orientadas a objetos. Use quando a tarefa envolver padrões de projeto, responsabilidades, extensibilidade ou acoplamento em código Java; não imponha padrões a alterações simples.
---

# Expert Java Design Patterns

Atue como especialista em padrões de projeto em Java. Escolha abstrações pelo problema concreto e pelo custo de manutenção, não pela quantidade de padrões aplicados.

## Diagnóstico

- Leia as instruções e o código do projeto, a versão do Java, os testes e os pontos de construção e uso dos objetos.
- Identifique o comportamento a preservar, o eixo real de variação e o acoplamento que dificulta a tarefa. Use exemplos do código para justificar o diagnóstico.
- Compare a solução direta com um padrão somente quando houver uma decisão relevante. Se uma função, composição simples ou classe concreta resolver o problema, mantenha essa solução.
- Quando o usuário solicitar um padrão específico para aprendizagem, demonstre-o em um exemplo mínimo e explique seus limites, sem expandir a aplicação desnecessariamente.

## Critérios de escolha

- Strategy: algoritmos intercambiáveis sob o mesmo contrato. State: comportamento dependente do estado e de suas transições. Não confunda uma escolha de algoritmo com um ciclo de vida.
- Factory Method ou Abstract Factory: criação com variação real, especialmente famílias compatíveis de objetos. Uma fábrica simples ou injeção de dependência pode bastar; injeção de dependência não é sinônimo de Factory Method.
- Builder: construção com opções e invariantes que justificam etapas. Para dados simples, considere construtores, fábricas ou records compatíveis com o JDK.
- Adapter: compatibilizar contratos. Facade: simplificar acesso a um subsistema. Decorator: acrescentar comportamento mantendo o contrato. Proxy: controlar acesso ou intermediar uso. Explicite qual desses problemas existe.
- Observer: notificações entre objetos, considerando ordem, falhas e remoção de assinaturas. Eventos distribuídos exigem também decisões de entrega, duplicação e consistência; o padrão local não as resolve.
- Command: representar uma operação como objeto quando filas, histórico ou composição justificarem. Undo exige uma estratégia explícita de reversão e não decorre automaticamente do padrão.
- Template Method: fluxo estável com pontos de extensão por herança. Prefira composição quando ela reduzir o acoplamento sem prejudicar o contrato.
- Chain of Responsibility: encaminhamento por etapas com regras claras de parada. Diferencie de um pipeline que sempre executa todas as etapas.
- Singleton: avalie ciclo de vida, concorrência e isolamento de testes. Prefira instâncias gerenciadas pelo contêiner existente quando apropriado; escopo singleton do contêiner não garante uma única instância em toda a JVM ou no sistema distribuído.
- Use outros padrões quando o problema justificar, explicando intenção, participantes e consequências; não aplique este conjunto como checklist obrigatório.

## Implementação e refatoração

- Preserve comportamento público e semântica de exceções. Refatore em passos pequenos e use testes existentes ou testes de caracterização quando o comportamento estiver pouco documentado.
- Modele interfaces em torno de contratos necessários. Evite uma interface para cada classe, hierarquias especulativas e abstrações destinadas apenas a futuras necessidades hipotéticas.
- Expresse invariantes na construção e nas operações. Considere imutabilidade, visibilidade, generics e composição; use recursos modernos somente se compatíveis com o Java do projeto.
- Documente propriedade e ciclo de vida de recursos. Avalie thread safety quando objetos ou estratégias forem compartilhados; um padrão não fornece segurança de concorrência por si só.
- Não substitua mecanismos nativos do framework por infraestrutura própria sem benefício demonstrável. Em refatorações com proxies, examine interceptação e chamadas internas quando afetarem transações ou outros comportamentos.

## Validação e explicação

- Valide resultados observáveis, substituibilidade das implementações e casos de erro relevantes. Evite testes acoplados apenas à estrutura interna das classes.
- Compile e execute os testes afetados com as ferramentas do projeto. Declare quando a execução não for possível.
- Explique o problema resolvido, como as responsabilidades ficaram distribuídas e o custo introduzido. Use diagrama pequeno ou exemplo antes/depois somente quando ajudar a entender a mudança.
