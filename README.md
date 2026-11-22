# Gestor de Clientes — versão conectada ao Supabase

Aplicação React + Vite com login Supabase e armazenamento na nuvem. A interface é responsiva para celular e computador.

## Configuração local

1. Instale Node.js.
2. Execute `npm install`.
3. Copie `.env.example` para `.env`.
4. Preencha `VITE_SUPABASE_URL` com a URL do projeto e `VITE_SUPABASE_ANON_KEY` com a chave publicável (sb_publishable_... ou anon pública).
5. Execute `npm run dev`.

## Publicar na Netlify

Conecte o repositório GitHub à Netlify e configure em Site configuration > Environment variables:
- `VITE_SUPABASE_URL`
- `VITE_SUPABASE_ANON_KEY`

Build command: `npm run build`; publish directory: `dist`.

## Banco de dados esperado

Usa as tabelas `customers`, `services` e `quotes` criadas no projeto Supabase. Cada inserção inclui o `user_id` da sessão; as políticas RLS do banco devem continuar habilitadas. Nunca use a chave `service_role` ou `secret` no navegador.

- customers: name, phone, address, notes, user_id
- services: customer_id, service_name, description, service_date, price, return_interval_days, user_id
- quotes: customer_id, description, amount, status, user_id

O login utiliza um usuário já criado no Supabase Authentication. O cadastro de usuários não é aberto pelo aplicativo.

## Limitações atuais

O botão WhatsApp abre uma conversa com texto preenchido; não envia mensagens automaticamente. O formulário de cliente usa nome, telefone e observações (a tabela SQL inicial não possui coluna de e-mail). O status de orçamento começa como pendente.
