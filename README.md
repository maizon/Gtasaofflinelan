# GTA San Andreas Android — Offline LAN Multiplayer

Projeto experimental para investigar e desenvolver multiplayer local (LAN/Wi-Fi sem internet) para GTA: San Andreas clássico no Android, priorizando compatibilidade, segurança e validação reproduzível.

> **Estado atual: scaffold inicial.** Este repositório ainda não contém integração funcional com o jogo, sincronização de jogadores nem APK. Não confunda o plano com funcionalidades implementadas.

## Objetivo

Permitir que dois ou mais dispositivos na mesma rede local joguem juntos, começando por uma prova de conceito de descoberta/conexão e sincronização de estado. O objetivo final é exibir jogadores remotos dentro do mundo do GTA SA Android, não apenas em uma tela de chat separada.

## Princípios

- LAN sem depender de servidores externos ou internet; um telefone pode hospedar a sessão.
- Não exigir root como meta de projeto, mas confirmar tecnicamente as limitações reais do Android.
- Compatibilidade baseada em evidências para versões específicas do jogo e ABIs; não presumir que mods de PC funcionem no Android.
- Separar app Android, protocolo de rede e integração nativa com o jogo.
- Não distribuir APKs, bibliotecas, assets ou outros arquivos proprietários do jogo.
- Não afirmar que algo funciona sem testes e evidências registrados.

## Estado e próximas etapas

1. **Auditoria** — estudar CoopAndreas e projetos SA-MP relacionados, registrando licença, plataforma, dependências, build e possibilidade real de reaproveitamento.
2. **Inventário de compatibilidade** — identificar versão exata do GTA SA Android, ABI (`armeabi-v7a`/`arm64-v8a`), versão do Android e limitações de carregamento de código nativo.
3. **Prova de conceito de rede** — criar host/cliente LAN independente do jogo, com descoberta, conexão, heartbeat, timeout e testes de dois dispositivos.
4. **Protocolo** — definir mensagens versionadas, IDs de sessão/jogador, validação de pacotes e atualização de estado.
5. **Integração no jogo** — somente após identificar pontos de entrada e estruturas corretas na versão-alvo; começar pela criação/atualização de um jogador remoto.
6. **Expansão** — animações, veículos, combate e outros sistemas por etapas, com critérios de teste próprios.

## Documentação

- [Plano técnico](docs/PLAN.md)
- [Auditoria de referências](docs/REFERENCE_AUDIT.md)
- [Protocolo de rede](docs/PROTOCOL.md)
- [Matriz de testes](docs/TEST_PLAN.md)
- [Estado do projeto](STATUS.md)

## Requisitos para avançar

Precisamos registrar a versão exata do jogo instalada em cada dispositivo, arquitetura/ABI, versão do Android, fabricante/SoC e se é permitido usar uma biblioteca nativa carregada pelo jogo. Não publique APK/OBB nem dados privados do dispositivo no repositório.

## Licença

A licença do código original deste projeto deverá ser definida antes de incorporar código de terceiros. Cada referência deve ser auditada separadamente; não copie código sem confirmar licença e obrigações de atribuição.

## Aviso

Projeto comunitário, experimental e não oficial. Grand Theft Auto e GTA: San Andreas são marcas de seus respectivos titulares. Este projeto não é afiliado à Rockstar Games.