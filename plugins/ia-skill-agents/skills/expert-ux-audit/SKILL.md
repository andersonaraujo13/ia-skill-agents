---
name: expert-ux-audit
description: Audite imagens e referências de interfaces web ou móveis, identificando problemas de UX/UI e entregando um prompt técnico para refatoração front-end. Use quando o usuário enviar prints, mockups ou referências visuais para revisão.
---

# Auditoria UX/UI

Analise diretamente cada imagem, print ou referência visual fornecida. A entrega é uma orientação prática para implementação no front-end, não uma crítica genérica de design.

## Critérios de análise

Examine somente problemas que estejam visíveis ou que sejam inferências razoáveis da interface:

- usabilidade e fluxo: clareza de ações, estados, feedback, densidade e esforço para completar tarefas;
- hierarquia visual: destaque do objetivo principal, escaneabilidade, agrupamentos e ordem de leitura;
- layout: alinhamento, espaçamento, grid, proximidade, responsividade aparente e áreas de toque;
- tipografia: escala, pesos, legibilidade, comprimento de linha e consistência;
- acessibilidade: contraste aparente, tamanho de texto e controles, dependência exclusiva de cor, foco e rótulos quando identificáveis;
- UI: consistência de componentes, cores, bordas, ícones, botões, superfícies e estados visuais.

Não invente requisitos de negócio, problemas de código ou conformidade que a referência não sustente. Diferencie observações certas de recomendações condicionais quando a imagem não mostrar estados, breakpoints ou interações.

## Formato obrigatório da resposta

Responda em português, de forma direta e concisa, com exatamente estas duas partes:

1. **Diagnóstico UX/UI**: lista de marcadores com problemas observáveis e seu impacto. Priorize os itens de maior efeito na tarefa do usuário. Agrupe pontos semelhantes e evite recomendações vagas como "melhorar a experiência".
2. **Prompt técnico para refatoração**: um único bloco de código, pronto para copiar, que instrua um gerador de código front-end a corrigir todos os pontos diagnosticados.

O prompt técnico deve:

- definir o objetivo e preservar a finalidade atual da página;
- transformar cada diagnóstico em instruções implementáveis de layout, componentes, tipografia, cores, responsividade e acessibilidade;
- pedir HTML/CSS/JS ou o framework já presente no projeto, sem impor tecnologia se ela não foi informada;
- incluir requisitos verificáveis, como foco visível, contraste adequado, labels acessíveis, estados de interação e comportamento em telas menores quando aplicável;
- preservar conteúdos, rotas, integrações e regras de negócio existentes, salvo solicitação contrária;
- solicitar código organizado, responsivo e sem alterar funcionalidades não relacionadas.

Quando não houver imagem ou referência acessível, peça que o usuário a envie antes de auditar. Quando houver contexto de código junto da imagem, adapte o prompt às tecnologias e aos componentes existentes.
