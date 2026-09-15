# IA Skills & Agents

Repositório pessoal de skills e agentes para desenvolvimento, revisão e auditoria de software. A mesma fonte atende Claude Code e Codex.

## Estrutura

- `skills/`: skills compartilhadas pelos dois agentes.
- `agents/`: definições do agente `revisor-codigo-java`; o Markdown é usado pelo Claude Code e o TOML pelo Codex.
- `.claude-plugin/plugin.json`: manifesto do plugin Claude Code.
- `.codex-plugin/plugin.json`: manifesto do plugin Codex.

## Atualização

Atualize este clone com `git pull`. O Claude Code usa o plugin a partir deste repositório. Para o Codex, reinstale o plugin após atualizar, para que ele recarregue as skills e a definição do agente.

As skills têm uma única cópia em `skills/`; não copie nem mantenha versões em `~/.codex/skills`, pois isso cria divergência.
