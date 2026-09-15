# Catálogo de decisão para padrões Java

Consulte apenas a família relacionada ao problema atual. Este catálogo orienta decisões; não é uma lista de padrões obrigatórios.

## Criação

- **Factory Method / Abstract Factory:** escolha variável de implementação ou família coerente de objetos. Evite para encapsular um único `new` estável.
- **Builder:** muitos parâmetros opcionais, invariantes de construção ou etapas legíveis. Prefira construtor ou factory nomeada para valores pequenos e obrigatórios.
- **Prototype:** cópia configurável de objetos caros ou complexos; avalie primeiro factories e objetos imutáveis.
- **Singleton:** somente quando unicidade fizer parte do domínio ou runtime. Em Spring, prefira o escopo do container e evite estado global mutável.

## Estrutura

- **Adapter:** traduz um contrato externo para o contrato esperado pela aplicação.
- **Facade:** oferece entrada coesa para um subsistema complexo.
- **Decorator:** combina responsabilidades transversalmente e em runtime; avalie proxies, filtros e interceptors do framework.
- **Composite:** representa hierarquias parte-todo com tratamento uniforme.
- **Proxy:** controla acesso, lazy loading, transações ou chamadas remotas; considere Spring e Hibernate.
- **Bridge:** separa duas dimensões que variam independentemente, quando ambas forem reais.

## Comportamento

- **Strategy:** substitui condicionais entre algoritmos ou políticas intercambiáveis.
- **State:** modela transições e comportamento por estado quando enum e tabela de transição já não bastam.
- **Command:** representa operação como dado, útil para filas, auditoria, retry ou undo.
- **Chain of Responsibility:** sequência extensível de handlers; mantenha ordem e parada explícitas.
- **Template Method:** esqueleto estável com etapas variáveis; prefira composição quando herança criar acoplamento.
- **Observer / Domain Event:** comunica fatos a interessados; defina sincronia, transação, falha e idempotência.
- **Specification:** compõe regras e critérios de consulta reutilizáveis; evite para validações simples.
- **Mediator:** coordena interações complexas e evita dependências muitos-para-muitos.

## Domínio e arquitetura

- **Value Object:** valor imutável e validado, sem identidade própria.
- **Entity:** objeto com identidade e ciclo de vida; considere as limitações do ORM.
- **Aggregate:** fronteira de consistência com raiz responsável por invariantes. Nem toda relação JPA forma um agregado.
- **Domain Service:** regra de domínio que não pertence naturalmente a entidade ou value object.
- **Application Service / Use Case:** coordena fluxo, transação, autorização e portas sem detalhes de transporte.
- **Repository:** abstrai persistência de agregados ou consultas quando melhora o modelo.
- **Hexagonal / Ports and Adapters:** protege o núcleo de múltiplas interfaces e infraestruturas. Evite multiplicar camadas em CRUD simples.
- **Anti-Corruption Layer:** impede que modelos externos contaminem o domínio.
- **CQRS:** separa leitura e escrita quando possuem necessidades realmente diferentes; não exige Event Sourcing.

## Integração e resiliência

- **Outbox:** publica eventos consistentemente com a transação do banco, aceitando entrega ao menos uma vez.
- **Idempotent Consumer:** torna reprocessamento seguro por chave, estado ou operação idempotente.
- **Saga:** coordena transações distribuídas com compensações e estados intermediários explícitos.
- **Circuit Breaker, Retry e Timeout:** protegem integrações. Retry exige segurança e backoff; timeout limita recursos.
- **Cache-Aside:** aplicação controla leitura e invalidação; defina fonte de verdade, TTL e tolerância a dados obsoletos.

## Sinais de sobreengenharia

- Interface e implementação únicas sem fronteira arquitetural ou necessidade de substituição.
- Factory que apenas chama um construtor simples.
- Builder que permite estados inválidos ou substitui poucos parâmetros obrigatórios.
- Evento usado para esconder uma chamada local que deveria ser explícita.
- Arquitetura hexagonal cheia de mapeamentos, mas sem núcleo independente ou adapters alternativos.
- Strategy ou State com muitas classes para dois casos estáveis que um enum comportamental resolveria.
- Nomes de patterns substituindo nomes do domínio.
