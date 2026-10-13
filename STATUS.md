# Estado do projeto

Última atualização: 2026-10-13

## Situação

O repositório foi inicializado com documentação de arquitetura, etapas, auditoria, protocolo proposto e plano de testes. **Ainda não existe implementação executável** e nenhuma funcionalidade de multiplayer no jogo foi validada.

## Entregue

- [x] Objetivo e limites documentados.
- [x] Plano de desenvolvimento por etapas.
- [x] Lista inicial de projetos para auditoria.
- [x] Protocolo conceitual para a prova de conceito LAN.
- [x] Critérios de teste para rede e futura integração nativa.

## Bloqueios atuais

- [ ] Identificar versão exata do GTA SA Android a suportar.
- [ ] Completar auditoria de código e licenças das referências.
- [ ] Confirmar caminho viável de integração nativa sem root.
- [ ] Implementar app de teste LAN.
- [ ] Testar em dois dispositivos físicos.

## Próxima tarefa

Auditar as referências e escolher uma estratégia baseada em código verificável. Em paralelo, registrar os dados técnicos do jogo-alvo (versão, ABI e Android). Não implementar offsets ou hooks específicos antes de confirmar a versão exata do binário.