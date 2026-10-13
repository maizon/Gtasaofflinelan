# Auditoria das referências

Esta página é um registro de auditoria, não uma declaração de compatibilidade. Os repositórios devem ser examinados no estado atual antes de copiar código. As licenças, branches e dependências podem mudar.

## Referências iniciais

| Projeto | URL | Perguntas a responder | Estado |
|---|---|---|---|
| CoopAndreas | https://github.com/Tornamic/CoopAndreas | Plataforma-alvo? Como injeta/integra? Protocolo? Dependências? Licença? | Pendente |
| SAMP-Mobile | https://github.com/kuzia15/SAMP-Mobile | Cliente Android real ou pacote/launcher? Versão do jogo? Licença? | Pendente |
| gta-reversed-android | https://github.com/gta-android/gta-reversed-android | Qual versão/ABI? É reimplementação, port ou ferramentas? Reutilizável? | Pendente |
| sampdroid | https://github.com/shadergz/sampdroid | Plataforma e versão suportadas? Dependências e licença? | Pendente |
| SA-MP-Mobile | https://github.com/sampapk/SA-MP-Mobile | Relação com outros forks, estado do código e compatibilidade? | Pendente |
| SA-MP-Android | https://github.com/SA-MP-Android/App | Componentes disponíveis, licenças e viabilidade de integração? | Pendente |

## Checklist por repositório

- [ ] Confirmar URL, branch padrão, atividade recente, tags e releases.
- [ ] Ler `README`, `LICENSE`, `NOTICE`, submódulos e instruções de build.
- [ ] Inventariar linguagem, NDK/SDK, ABI, versão-alvo do jogo e dependências.
- [ ] Identificar se o projeto depende de APK modificado, root, loader, scripts externos ou servidor de internet.
- [ ] Encontrar implementação real de transporte, handshake, entidades e sincronização; distinguir código funcional de documentação.
- [ ] Verificar compatibilidade de licenças antes de copiar, modificar ou combinar código.
- [ ] Registrar arquivos relevantes e evidência verificável (caminho/linha/commit).
- [ ] Classificar cada conclusão como **confirmada**, **provável** ou **não verificada**.

## Decisão de reaproveitamento

Não escolher uma base apenas pelo nome ou por existir um APK. A base deve demonstrar: código acessível, licença compatível, integração com a versão Android-alvo, build reproduzível e mecanismos relevantes para LAN. Se nenhuma satisfizer isso, usar apenas ideias/protocolos documentados e implementar componentes próprios.

## Modelo de registro

Para cada projeto, preencher:

- Commit/branch auditado:
- Licença e obrigações:
- Plataformas e versões:
- Build reproduzível:
- Componentes de rede:
- Integração com o jogo:
- Dependência de root/loader/patch:
- Código reutilizável e arquivos:
- Limitações e riscos:
- Conclusão e nível de confiança: