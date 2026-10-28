# Sinpla Odontologia

Landing page demonstrativa em português, adaptada do modelo de `AGENTE.md`. React, TypeScript, Vite, Tailwind CSS, Motion, Radix Accordion e Lucide. Layout responsivo, filtros de tratamentos, detalhes expansíveis, FAQ acessível, menu móvel e botões de WhatsApp.

## Executar

Requer Node.js 22.12+ ou 24.

```sh
npm ci
npm run dev
```

```sh
npm run build
npm run preview
```

O resultado publicável fica em `dist/`. O endereço relativo dos assets funciona no GitHub Pages e na HostGator.

## GitHub Pages

Crie um repositório público e envie estes arquivos, incluindo `package-lock.json`. Na configuração do repositório, em **Settings → Pages → Source**, escolha **GitHub Actions**. O workflow incluído publica a branch `main`. Não envie `node_modules`, `.env` ou credenciais. O projeto ainda não foi enviado nem publicado por este trabalho.

## HostGator

Execute `npm run build` e envie **o conteúdo** de `dist/` para a pasta pública do domínio (normalmente `public_html`) pelo gerenciador de arquivos ou SFTP. Inclua o `.htaccess`, que pode ficar oculto. Ative o certificado SSL e o redirecionamento HTTPS no painel. Não envie código de desenvolvimento, documentos de briefing, `node_modules` ou segredos para a pasta pública. Não é necessário Node.js no servidor.

## Informações e revisão com o cliente

- Nome, serviços, endereço e WhatsApp foram extraídos da captura do perfil fornecida. O Instagram não pôde ser consultado automaticamente.
- O link usa exatamente `553284143096`, conforme a captura. Confirmar o número e testar com a clínica antes de divulgar; não foi acrescentado um nono dígito por suposição.
- Endereço: Av. Presidente Itamar Franco, 1545, Juiz de Fora, CEP 36016-320. Confirmar complemento e horários.
- Imagens externas do Unsplash são ilustrativas. Substituir por fotos autorizadas da clínica antes do lançamento institucional. A marca tipográfica e o símbolo de folha são uma interpretação para a proposta, não uma reprodução do logotipo oficial.
- Não foram inventados depoimentos, avaliações, profissionais, registros, preços ou estatísticas. A versão demonstrativa está identificada no rodapé.
- Solicitar os dados institucionais, responsável técnico e registros profissionais aplicáveis para a revisão final do cliente antes do uso institucional.
- Dados de contato e textos ficam em `src/main.tsx`; cores e layout, em `src/style.css`.

## Segurança e privacidade

Aplicação estática sem autenticação, banco, uploads, formulários ou APIs próprias. Não coleta dados de saúde nem inclui rastreamento. Há aviso de privacidade e links externos com `noopener noreferrer`. A configuração Apache inclui CSP e cabeçalhos defensivos; verificar sua aplicação na hospedagem. O GitHub Pages não aplica `.htaccess`. As fotos externas implicam requisições ao Unsplash; para eliminar essa dependência, hospedar localmente imagens autorizadas e ajustar os caminhos. Recursos de backend do guia de segurança não se aplicam a esta versão. Dependências devem ser revisadas periodicamente com `npm audit`.
