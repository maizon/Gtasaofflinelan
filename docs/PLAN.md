# Plano técnico

## Alvo inicial

- Arquitetura pretendida: Android ARM64 (`arm64-v8a`). Confirmar a ABI real do jogo, pois a arquitetura do celular não garante que o aplicativo instalado seja ARM64.
- Topologia: dois celulares na mesma rede Wi-Fi.
- Internet: não necessária para hospedar/entrar na sessão local.
- Versão do GTA SA: desconhecida; identificar antes de implementar hooks, offsets ou estruturas nativas.
- Root: não desejado; investigar e comprovar um caminho sem root.

## Arquitetura proposta

```text
Android app (Kotlin/Java)
  ├─ interface: hospedar / entrar / estado da sessão
  ├─ transporte LAN e descoberta
  ├─ protocolo versionado + validação
  └─ camada JNI (futura, somente após auditoria)
          │
          ▼
Native bridge (C/C++ NDK; futuro)
  └─ adaptador específico para a versão do GTA SA Android
          │
          ▼
Game runtime (entidades, transformações, animações)
```

A integração nativa ainda é uma hipótese a validar. O app separado consegue provar a rede, mas não cria por si só personagens dentro do jogo.

## Fase 0 — identificar versão e auditar

- [ ] Identificar o pacote real instalado e registrar `versionName`, `versionCode` e `primaryCpuAbi`.
- [ ] Registrar a versão do Android e a ABI de `libGTASA.so`/`libGame.so`, conforme o binário efetivamente instalado.
- [ ] Auditar as referências e suas licenças antes de reutilizar código.
- [ ] Definir um único alvo inicial; não tentar suportar todas as versões simultaneamente.
- [ ] Criar relatório local de símbolos, imports, exports e hashes; não publicar arquivos proprietários do jogo.

Com ADB e depuração USB autorizada, uma tentativa inicial é:

```sh
adb devices
adb shell dumpsys package com.rockstargames.gtasa | grep -E 'versionName=|versionCode=|primaryCpuAbi='
```

Se o pacote não for encontrado, identificar o package name correto primeiro. Não compartilhar APK, OBB ou dados pessoais; apenas a versão e ABI relevantes.

**Saída obrigatória:** relatório de compatibilidade e decisão fundamentada sobre o mecanismo de integração.

## Fase 1 — prova de conceito LAN

- [ ] Aplicativo Android mínimo com modos Host e Entrar.
- [ ] Descoberta por UDP broadcast/multicast, com entrada manual por IP como fallback.
- [ ] Sessão local sem internet em dois celulares conectados ao mesmo Wi-Fi.
- [ ] Mensagens de handshake com versão do protocolo e nonce da sessão.
- [ ] Heartbeat, timeout, reconexão e encerramento limpo.
- [ ] Testes automatizados do parser e teste manual em dois aparelhos.

Critério de sucesso: dois dispositivos estabelecem sessão sem internet, exibem um ao outro na lista de jogadores e mantêm a conexão durante 10 minutos.

## Fase 2 — sincronização simulada

- [ ] Modelo de estado independente do jogo: ID, posição 3D, heading, estado básico e timestamp.
- [ ] Atualização frequente por UDP, com sequência e descarte de pacotes antigos.
- [ ] Canal confiável para eventos discretos quando necessário.
- [ ] Interpolação no cliente; não usar posição recebida diretamente sem validar limites e formato.
- [ ] Simulação de perda, latência, pacotes duplicados e cliente desconectado.

Critério de sucesso: dois clientes veem marcadores simulados moverem-se de forma estável e consistente.

## Fase 3 — primeiro personagem remoto no jogo

- [ ] Identificar funções/estruturas corretas para a versão e ABI alvo.
- [ ] Determinar um ponto de integração permitido e tecnicamente viável sem root.
- [ ] Implementar adaptador nativo isolado por versão.
- [ ] Criar e remover um personagem remoto de teste.
- [ ] Atualizar posição/heading no thread apropriado do jogo.
- [ ] Evitar chamadas à engine a partir da thread de rede.
- [ ] Testar colisão, streaming do mundo, respawn e encerramento.

Não avançar para sincronização completa até o primeiro personagem remoto ser criado e removido sem crash em testes repetidos.

## Fase 4 — funcionalidades por etapas

1. Posição e orientação.
2. Animações básicas e estados de movimento.
3. Entrada/saída de veículos e sincronização de veículos.
4. Saúde, armas e eventos de combate.
5. Chat e gerenciamento de sessão.
6. Cooperação em missões, apenas após avaliar conflitos com scripts e estado de missão local.

## Restrições técnicas importantes

- GTA SA para PC usa mecanismos de modificação diferentes do APK Android; DLLs/ASI de PC não são automaticamente compatíveis.
- Android moderno restringe execução/carregamento de código e acesso a diretórios privados. Sem root, o caminho depende da forma como o jogo pode carregar a biblioteca ou ser iniciado por um launcher compatível.
- A versão do jogo pode alterar endereços, símbolos, layouts e ABI. Não usar offsets sem identificar versão e validar.
- O host deve ser autoritativo para IDs e eventos de sessão; ainda assim, o protótipo não deve ser exposto à internet.
- Nenhum teste é considerado aprovado sem versão, dispositivo, passos e resultado registrados.