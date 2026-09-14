---
name: expert-java-security
description: Auditar segurança de aplicações Java e produzir achados priorizados com evidências e recomendações, sem alterar código ou configurações para remediação. Use em revisões de segurança Java e no agente revisor-codigo-java.
---

# Auditoria de segurança Java sem remediação

Esta skill produz diagnóstico. Não altere código-fonte, testes, dependências, lockfiles ou configurações para corrigir segurança. Não aplique patches, atualizações de CVEs ou hardening. Sugira a correção em linguagem clara no relatório. Análises podem gerar relatórios e caches locais; não use modos auto-fix. Se outra tarefa autorizar refatorações, essa autorização não abrange remediar os achados desta auditoria.

## Análise orientada por evidências

Mapeie pontos de entrada, atores, recursos protegidos, fronteiras de confiança e dados sensíveis. Leia configuração efetiva e perfis relevantes sem expor valores de segredos. Rastreie entrada até o ponto de uso e verifique controles existentes antes de afirmar vulnerabilidade.

- Autenticação, sessão e tokens: validação de assinatura e claims aplicáveis, expiração, cookies, logout, armazenamento de senhas e bypass de filtros.
- Autorização: acesso por objeto, operação e tenant, escalada de privilégios, métodos internos e mass assignment. Não trate autenticação ou ocultação da interface como autorização.
- Injeção SQL/JPQL, comandos, templates e expressões; desserialização não confiável, XML/XXE e mecanismos de reflexão expostos. Verifique parametrização e sanitização no contexto de uso.
- SSRF, redirecionamentos, traversal, uploads e extração de arquivos: destinos efetivos, caminhos resolvidos, limites e controles de acesso.
- CSRF conforme cookies/autenticação; CORS conforme origens e credenciais; XSS conforme saída e consumidor. Não conclua vulnerabilidade apenas pela ausência de uma configuração sem analisar o fluxo.
- Criptografia, TLS, geração de valores sensíveis, segredos, logs, respostas de erro e endpoints de administração/diagnóstico expostos.
- Abuso de recursos: entradas e consultas sem limites, expressões regulares custosas e operações sensíveis sujeitas a repetição ou concorrência.
- Dependências: identifique versões resolvidas e transitivas e confirme advisories em fontes primárias atuais (fornecedor/projeto e registros oficiais). Diferencie versão potencialmente afetada de caminho explorável confirmado. Se não houver acesso à fonte, marque a verificação como pendente; não invente CVEs ou versões corrigidas.

Use ferramentas existentes em modo de análise, com resultados locais. Não envie código/segredos a serviços externos nem execute exploração contra sistemas reais como parte desta revisão. Comprove por inspeção ou verificações locais não destrutivas no escopo autorizado; não altere arquivos do projeto para criar provas. Registre incerteza quando condições de implantação não forem observáveis.

## Relatório final obrigatório

Ordene achados por risco contextual. Para cada achado, forneça severidade e justificativa, arquivo e linha verificados, evidência sanitizada, pré-condições, impacto, recomendação e estado confirmado ou a confirmar. Não reproduza credenciais; indique apenas localização e tipo.

Informe superfícies verificadas e lacunas (configuração de produção, infraestrutura, dependências ou fluxos não acessíveis). Se nada for identificado, limite a conclusão ao escopo revisado. Não declare o sistema seguro por ter compilado, passado testes ou não apresentado alertas em uma ferramenta.
