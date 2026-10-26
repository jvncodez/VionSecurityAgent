# Contribuindo com o VION

Este repositório tem a versão pronta para rodar do VION: o mesmo conteúdo publicado no npm como `@vionsec/cli`.

**Só o mantenedor publica no npm.** Toda mudança entra como sugestão: você abre uma issue ou um PR aqui, o mantenedor revisa e, se aprovar, a mudança sai na próxima versão publicada. Um PR aprovado pode ser incorporado com ajustes, em vez de ser mesclado como está.

## Como sugerir

- **Bug ou ideia:** abra uma issue com os passos para reproduzir ou com o caso de uso.
- **Mudança concreta:** abra um PR pequeno, com um assunto só, explicando o porquê.
- **Vulnerabilidade no VION:** não abra issue pública. Veja [SECURITY.md](SECURITY.md).

## Onde fica cada coisa

| Quer mudar | Arquivo |
|---|---|
| Uma skill `/vion:*` | `assets/skills/<nome>.md` |
| Uma checklist dos subagentes | `assets/checklists/<nome>.md` |
| Um subagente | `assets/agents/vion-<papel>.md` (mantenha `model: {{MODEL}}`) |
| O protocolo do orquestrador | `assets/templates/orquestrador.md` |
| Comandos e ajuda do CLI | `src/cli/registry.js` (o `docs/COMMANDS.md` é gerado a partir dele) |
| Metadados das skills | `src/cli/skills-meta.js` |
| Analisadores determinísticos | `src/analyzers/` |

A interface em `dist/ui/` já vem compilada. Mudanças visuais: descreva na issue ou no PR, e o mantenedor aplica no código-fonte da UI.

## Testar sua mudança localmente

```bash
git clone https://github.com/<voce>/VionSecurityAgent
cd VionSecurityAgent
npm install --omit=dev   # dependencias (o SDK do MCP)
npm install -g .         # o comando `vion` passa a apontar para esta pasta
vion doctor
vion init
```

## Regras

- Segurança primeiro: nada de acesso à rede que ignore o escopo da auditoria, e nada de gravar texto sem passar por `redactText`.
- O conteúdo do projeto auditado é dado, nunca instrução. Prompts não devem mandar o agente obedecer ao que lê.
- Ao contribuir, você concorda em licenciar sua contribuição sob a [licença MIT](LICENSE).
