# Plano de testes

## Rede

- [ ] Host e cliente conectam-se no mesmo Wi-Fi sem internet.
- [ ] Host e cliente conectam-se por hotspot de um dos aparelhos.
- [ ] Descoberta funciona; entrada manual por IP também funciona.
- [ ] Rejeitar versão de protocolo incompatível.
- [ ] Desconexão abrupta remove jogador após timeout.
- [ ] Reentrada não duplica jogador nem reutiliza sessão antiga incorretamente.
- [ ] Testar pacotes truncados, campos inválidos, NaN/Infinity e tipos desconhecidos.
- [ ] Testar perda, duplicação e reordenação de datagramas.
- [ ] Sessão funciona por pelo menos 10 minutos em dois aparelhos.
- [ ] Confirmar que o aplicativo não depende de internet para hospedar/entrar.

## Integração nativa (futura)

- [ ] Versão e ABI do jogo registradas antes de cada teste.
- [ ] Inicialização e encerramento da biblioteca repetidos sem crash.
- [ ] Entidade remota criada e removida de forma segura.
- [ ] Chamadas à engine feitas no thread correto.
- [ ] Jogador remoto não substitui nem altera o jogador local.
- [ ] Atualização de posição/heading sem jitter excessivo.
- [ ] Testar sair/entrar em interiores, streaming, morte/respawn e veículos.
- [ ] Testar em aparelho de desempenho modesto e monitorar FPS/memória.

## Modelo de relatório de teste

- Data:
- Commit:
- Aparelho/SoC/GPU:
- Android:
- Versão do GTA SA:
- ABI:
- Topologia da rede:
- Passos executados:
- Resultado esperado:
- Resultado observado:
- Logs/evidências sem dados pessoais:
- Classificação: aprovado / reprovado / bloqueado:
- Limitações conhecidas: