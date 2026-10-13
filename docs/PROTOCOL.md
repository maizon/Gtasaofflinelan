# Protocolo LAN — proposta inicial

**Estado:** rascunho; ainda não implementado. A versão inicial serve para orientar a prova de conceito e poderá mudar após testes.

## Transporte

- UDP para descoberta e atualizações frequentes de estado.
- TCP ou canal confiável equivalente para handshake/eventos que não podem ser perdidos, se a implementação demonstrar que isso simplifica a confiabilidade.
- Todos os dispositivos precisam estar na mesma LAN/hotspot; internet não deve ser necessária.
- Descoberta automática é opcional: conexão manual por IP deve continuar disponível.

## Mensagens conceituais

- `DISCOVER`: procura hosts na LAN.
- `ADVERTISE`: resposta com nome da sessão, versão do protocolo e capacidade atual.
- `HELLO`: cliente solicita entrada com versão compatível.
- `WELCOME`: host atribui ID de jogador e confirma a sessão.
- `HEARTBEAT`: mantém a conexão viva.
- `PLAYER_STATE`: posição, heading, estado e número de sequência.
- `PLAYER_EVENT`: evento discreto, por exemplo entrar/sair de veículo.
- `LEAVE`: saída voluntária.

## Regras de segurança e robustez

- Prefixo de protocolo com magic bytes, versão, tipo e tamanho do payload.
- Rejeitar mensagens com comprimento incorreto, tipos desconhecidos e valores não finitos.
- Limitar tamanho de datagrama e frequência de mensagens.
- Usar timeout e número de sequência; descartar estado atrasado ou repetido.
- Nunca aceitar ID de jogador escolhido livremente pelo cliente como autoridade.
- Não expor portas nem abrir encaminhamento de portas no roteador para a prova de conceito.
- Tratar nome de sessão e nickname como texto não confiável.

## Modelo de estado inicial

```text
PlayerState {
  player_id: uint16
  sequence: uint32
  timestamp_ms: uint32
  x: float32
  y: float32
  z: float32
  heading: float32
  movement_state: uint8
}
```

Este formato é ilustrativo, não um contrato final. A implementação deverá definir endianness, serialização, limites de coordenadas, frequência de atualização e compatibilidade de versões antes de usar os dados em qualquer função do jogo.

## Frequência e interpolação

Começar com atualização de estado entre 10 e 20 Hz e medir tráfego/latência em dispositivos reais. Renderização deve interpolar entre estados recebidos, não teletransportar a entidade a cada pacote. Valores finais devem ser decididos por medição, não por suposição.