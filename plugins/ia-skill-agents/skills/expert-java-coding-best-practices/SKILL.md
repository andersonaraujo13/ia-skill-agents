---
name: expert-java-coding-best-practices
description: Revisar e refatorar código Java para corrigir bugs, bad smells e problemas de manutenção com validação de comportamento. Use em revisões de qualidade e refatorações Java; não imponha mudanças cosméticas a tarefas sem esse escopo.
---

# Boas práticas de desenvolvimento Java

Inspecione JDK, build, convenções, instruções e testes antes de escolher uma solução. Priorize defeitos observáveis e custo real de manutenção; SOLID, DRY e simplicidade são critérios, não justificativas automáticas para criar abstrações.

## Diagnóstico e mudanças

- Examine métodos/classes com responsabilidades misturadas, duplicação de regra, condicionais complexas, excesso de parâmetros, acoplamento, dependências cíclicas, estado global e abstrações sem uso. Demonstre o problema no fluxo real; tamanho isolado não prova um smell. Não una regras apenas por semelhança textual.
- Revise nulidade, limites, coleções vazias, igualdade e hashCode, chaves mutáveis, contratos de comparação, generics/raw types, exposição de coleções e mutabilidade compartilhada. Preserve contratos públicos ao introduzir Optional, records ou imutabilidade.
- Verifique fechamento de recursos e propriedade de streams/conexões com try-with-resources quando apropriado. Não feche recurso pertencente ao chamador. Preserve causa e semântica de exceções; não engula falhas nem converta indiscriminadamente exceções em sucesso.
- Verifique interrupção, cancelamento, executores, races e atomicidade em estado compartilhado. Evite parallelStream ou bloqueios adicionados sem entender carga, transações e ciclo de vida.
- Em cálculos monetários/decimais, examine precisão, escala e arredondamento conforme a regra de negócio. Em datas, examine timezone e limites; não troque tipos ou defaults globais sem avaliar consumidores.
- Considere custo de consultas, loops e alocações quando houver evidência; não faça otimizações especulativas. Respeite limites transacionais e efeitos externos das operações existentes.
- Refatore em passos pequenos, preservando comportamento, compatibilidade de serialização e APIs. Justifique abstrações pelo uso atual. Evite dependências novas quando o JDK ou framework existente resolve.
- Ao reconhecer um problema de segurança em uma revisão com segurança somente diagnóstico, relate-o sem aplicar correção ou contornar a restrição sob o nome de refatoração.

## Validação

Use testes existentes e crie testes comportamentais de regressão para bugs e mudanças relevantes. Para refatorações arriscadas sem cobertura, caracterize o comportamento antes. Não faça testes que apenas reproduzem a estrutura da implementação.

Execute build e verificadores configurados (por exemplo Checkstyle, SpotBugs ou PMD) quando aplicáveis, sem instalar todos como obrigação. Confirme testes pertinentes, inclusive integração quando semântica do banco/framework estiver envolvida. Verifique o diff para mudanças acidentais e informe evidências, pendências e limitações sem atribuir a esta revisão uma cobertura que não teve.
