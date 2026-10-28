# Guia Mestre de Segurança para Aplicações Modernas (Vibe Coding)

> Documento consolidado reunindo boas práticas de segurança para
> aplicações desenvolvidas com apoio de IA, APIs, bancos de dados,
> autenticação, integrações e infraestrutura.

## Objetivos

-   Padronizar requisitos mínimos de segurança.
-   Servir como checklist antes de publicar qualquer aplicação.
-   Mitigar falhas comuns geradas por IA.

------------------------------------------------------------------------

# 1. Princípios Fundamentais

-   Segurança deve ser requisito explícito desde o início.
-   Aplicar Defesa em Profundidade.
-   Princípio do Menor Privilégio.
-   Nunca confiar em dados enviados pelo cliente.
-   Validar tudo no backend.
-   Pensar como um atacante antes da publicação.

------------------------------------------------------------------------

# 2. Autenticação

## Implementar

-   Argon2 ou bcrypt (+ salt)
-   MFA (principalmente administração)
-   Política forte de senhas
-   Bloqueio após tentativas
-   CAPTCHA quando necessário
-   JWT com expiração curta, refresh token e validação de assinatura
-   Logout invalida sessão
-   Cookies HttpOnly, Secure e SameSite

## Evitar

-   JWT sem expiração
-   Segredos fracos
-   Sessões eternas
-   Credenciais padrão

------------------------------------------------------------------------

# 3. Autorização

-   RBAC ou ABAC
-   Validar permissões em todas as rotas
-   Validar propriedade do recurso (evitar IDOR/BOLA)
-   Nunca confiar em role ou user_id enviados pelo cliente
-   Menor privilégio

------------------------------------------------------------------------

# 4. Banco de Dados

-   Prepared Statements
-   ORM parametrizado
-   Nunca concatenar SQL
-   Usuário do banco com privilégios mínimos
-   Foreign Keys
-   Constraints
-   Índices
-   Migrations
-   Soft Delete quando necessário
-   Auditoria
-   Backup
-   Criptografia em repouso
-   Bloquear Mass Assignment (whitelist)

------------------------------------------------------------------------

# 5. Validação de Entradas

-   Validar frontend e backend
-   Validar schema (Zod, Joi, class-validator...)
-   Sanitizar HTML
-   Escapar saída
-   CSP
-   Proteção contra XSS
-   Tokens CSRF
-   Validação de origem

------------------------------------------------------------------------

# 6. Upload de Arquivos

-   Validar MIME e Magic Bytes
-   Limitar tamanho
-   Renomear arquivos
-   Armazenar fora da pasta pública
-   Bloquear executáveis
-   Antivírus quando aplicável

------------------------------------------------------------------------

# 7. APIs

-   Rate Limit
-   Versionamento
-   Timeouts
-   Idempotência
-   Logs seguros
-   Nunca confiar apenas no frontend

------------------------------------------------------------------------

# 8. Webhooks

-   Assinatura HMAC
-   Timestamp
-   Nonce
-   Replay Protection
-   Idempotência
-   Retry controlado
-   Segunda validação antes de executar ações críticas

------------------------------------------------------------------------

# 9. Área Administrativa

-   MFA
-   Sessões curtas
-   Auditoria
-   RBAC
-   Confirmação de ações críticas
-   Troca obrigatória de senha no primeiro acesso
-   Restrição por IP/VPN quando possível

------------------------------------------------------------------------

# 10. Configuração

-   .env fora do Git
-   Secret Manager
-   HTTPS obrigatório
-   HSTS
-   CORS restritivo
-   Debug desligado em produção
-   Docker sem root
-   Firewall

------------------------------------------------------------------------

# 11. Logs, Auditoria e Observabilidade

## Nunca registrar

-   Senhas
-   Tokens
-   JWT
-   Cookies
-   Dados sensíveis

## Registrar

-   Usuário
-   Data/Hora
-   IP
-   Navegador
-   Valores antigos/novos

## Observabilidade

-   Logs
-   Métricas
-   Tracing
-   Alertas

------------------------------------------------------------------------

# 12. Recuperação de Senha

-   Token único
-   Expiração
-   Uso único

------------------------------------------------------------------------

# 13. LGPD

-   Consentimento
-   Exclusão
-   Exportação
-   Anonimização

------------------------------------------------------------------------

# 14. Dependências

-   Atualizações frequentes
-   Dependabot/Renovate
-   npm audit
-   Scanner de vulnerabilidades

------------------------------------------------------------------------

# 15. Testes Antes da Produção

-   SQL Injection
-   XSS
-   CSRF
-   IDOR/BOLA
-   Autorização
-   Upload
-   Webhooks
-   Pentest
-   Revisão manual independente
-   Testes pensando em usuário malicioso

------------------------------------------------------------------------

# 16. Falhas Mais Comuns Geradas por IA

-   Segurança não solicitada no prompt
-   SQL inseguro
-   JWT mal configurado
-   Rotas protegidas apenas no frontend
-   Falta de validação backend
-   CORS liberado
-   .env versionado
-   Logs sensíveis
-   Debug ativo
-   Falta de rate limiting
-   Falta de criptografia
-   Falta de verificação de propriedade
-   Webhooks sem autenticação

------------------------------------------------------------------------

# 17. Framework Mental

Antes de publicar, pergunte:

1.  Quem está fazendo a requisição?
2.  Pode executar esta ação?
3.  O recurso pertence ao usuário?
4.  Todas as entradas foram validadas?
5.  Há proteção contra SQL Injection, XSS e CSRF?
6.  APIs e Webhooks são autenticados?
7.  Segredos estão protegidos?
8.  Logs expõem dados?
9.  Existe auditoria?
10. Backup foi testado?
11. Existe monitoramento?
12. Está em conformidade com a LGPD?

------------------------------------------------------------------------

# Checklist Final

-   [ ] Autenticação segura
-   [ ] Autorização completa
-   [ ] Banco protegido
-   [ ] Inputs validados
-   [ ] Upload seguro
-   [ ] APIs protegidas
-   [ ] Webhooks validados
-   [ ] Área administrativa protegida
-   [ ] Infraestrutura endurecida
-   [ ] Logs seguros
-   [ ] Auditoria ativa
-   [ ] Backups testados
-   [ ] Dependências atualizadas
-   [ ] Pentest realizado
-   [ ] Revisão humana concluída

> Segurança não é uma funcionalidade. É uma característica de qualidade
> construída continuamente durante todo o ciclo de vida da aplicação.
