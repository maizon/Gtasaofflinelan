# GTA San Andreas Android — Offline LAN Multiplayer

Projeto experimental para investigar e desenvolver multiplayer local (LAN/Wi-Fi sem internet) para GTA: San Andreas clássico no Android, priorizando compatibilidade, segurança e validação reproduzível.

> **Estado atual: scaffold inicial.** Este repositório ainda não contém integração funcional com o jogo, sincronização de jogadores nem APK. Não confunda o plano com funcionalidades implementadas.

## Alvo inicial escolhido

- **Arquitetura desejada:** Android ARM64 (`arm64-v8a`).
- **Teste inicial:** dois celulares na mesma rede Wi-Fi, sem internet.
- **Versão do jogo:** ainda desconhecida; será identificada antes de qualquer hook, offset ou integração específica.
- **Root:** não é requisito desejado; viabilidade sem root precisa ser comprovada.

O primeiro marco será uma prova de conceito de rede local. Em seguida, a meta é exibir jogadores remotos dentro do mundo do jogo, não apenas em uma tela de chat separada.

## Princípios

- LAN sem depender de servidores externos ou internet; um telefone pode hospedar a sessão.
- Não exigir root como meta de projeto, mas confirmar tecnicamente as limitações reais do Android.
- Compatibilidade baseada em evidências para versões específicas do jogo e ABIs; não presumir que mods de PC funcionem no Android.
- Separar app Android, protocolo de rede e integração nativa com o jogo.
- Não distribuir APKs, bibliotecas, assets ou outros arquivos proprietários do jogo.
- Não afirmar que algo funciona sem testes e evidências registrados.

## Estado e próximas etapas

1. **Identificar a versão instalada** — coletar `versionName`, `versionCode` e ABI do pacote oficial em um dos celulares.
2. **Auditoria** — estudar CoopAndreas e projetos SA-MP relacionados, registrando licença, plataforma, dependências, build e possibilidade real de reaproveitamento.
3. **Inventário de compatibilidade** — registrar versão do Android e arquitetura do jogo; confirmar limitações de carregamento de código nativo.
4. **Prova de conceito de rede** — criar host/cliente LAN independente do jogo, com descoberta, conexão, heartbeat, timeout e testes nos dois celulares.
5. **Protocolo** — definir mensagens versionadas, IDs de sessão/jogador, validação de pacotes e atualização de estado.
6. **Integração no jogo** — somente após identificar pontos de entrada e estruturas corretas na versão-alvo; começar pela criação/atualização de um jogador remoto.
7. **Expansão** — animações, veículos, combate e outros sistemas por etapas, com critérios de teste próprios.

## Documentação

- [Plano técnico](docs/PLAN.md)
- [Auditoria de referências](docs/REFERENCE_AUDIT.md)
- [Protocolo de rede](docs/PROTOCOL.md)
- [Matriz de testes](docs/TEST_PLAN.md)
- [Estado do projeto](STATUS.md)

## Como identificar a versão do jogo

Se tiver ADB num computador com o celular conectado por USB e a depuração USB autorizada, execute:

```sh
adb devices
adb shell dumpsys package com.rockstargames.gtasa | grep -E 'versionName=|versionCode=|primaryCpuAbi='
```

O nome do pacote pode variar conforme a edição. Se não retornar dados, confirme o identificador do pacote no aparelho. Não envie APK/OBB nem dados pessoais; basta compartilhar as linhas de versão e ABI. Também é possível abrir as informações do aplicativo e informar a versão exibida, mas isso pode não revelar a ABI.

## Licença

A licença do código original deste projeto deverá ser definida antes de incorporar código de terceiros. Cada referência deve ser auditada separadamente; não copie código sem confirmar licença e obrigações de atribuição.

## Aviso

Projeto comunitário, experimental e não oficial. Grand Theft Auto e GTA: San Andreas são marcas de seus respectivos titulares. Este projeto não é afiliado à Rockstar Games.