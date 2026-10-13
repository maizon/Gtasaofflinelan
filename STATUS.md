# Estado do projeto

Última atualização: 2026-10-13

## Alvo definido pelo usuário

- Arquitetura desejada: ARM64 (`arm64-v8a`).
- Primeiro teste: dois celulares na mesma rede Wi-Fi.
- Internet: não deve ser necessária para criar e manter a sessão LAN.
- Versão do GTA SA Android: desconhecida e precisa ser identificada antes da integração nativa.
- Root: não desejado; caminho sem root ainda precisa ser comprovado.

## Situação

O repositório foi inicializado com documentação de arquitetura, etapas, auditoria, protocolo proposto e plano de testes. **Ainda não existe implementação executável** e nenhuma funcionalidade de multiplayer no jogo foi validada.

## Entregue

- [x] Objetivo e limites documentados.
- [x] Plano de desenvolvimento por etapas.
- [x] Lista inicial de projetos para auditoria.
- [x] Protocolo conceitual para a prova de conceito LAN.
- [x] Critérios de teste para rede e futura integração nativa.
- [x] Prioridades iniciais registradas: ARM64 e dois aparelhos no mesmo Wi-Fi.

## Bloqueios atuais

- [ ] Identificar versão exata do GTA SA Android e ABI real do binário instalado.
- [ ] Completar auditoria de código e licenças das referências.
- [ ] Confirmar caminho viável de integração nativa sem root.
- [ ] Implementar app de teste LAN.
- [ ] Testar em dois dispositivos físicos sem internet.

## Próxima tarefa

Identificar a versão do jogo no celular e auditar a referência SAMP-Mobile, que documenta branches separadas para GTA SA 2.10 e 2.11, incluindo ARM64. Não assumir que uma dessas versões é a instalada até confirmar os dados do aparelho. Depois, implementar a primeira prova de conceito de conexão LAN.