# Gestão e Controle — versão inicial

Aplicação web React + Vite + Supabase, com login real, dashboard e cadastros nas 10 tabelas já criadas no Supabase.

## 1. Configurar

Instale Node.js 20 ou superior. Descompacte este projeto e abra a pasta em um terminal.

Copie `.env.example` para `.env` e substitua `COLE_AQUI_SUA_CHAVE_sb_publishable` pela **chave publicável** (`sb_publishable_...`) do projeto Supabase. A URL do projeto já está preenchida com base nas capturas de tela. **Nunca use `service_role` ou `sb_secret_` no navegador.**

## 2. Executar localmente

```bash
npm install
npm run dev
```

Abra a URL indicada pelo terminal (geralmente http://localhost:5173).

## 3. Login

Entre com o e-mail e a senha de um usuário já cadastrado em Supabase Authentication. Um usuário convidado precisa primeiro aceitar o convite e definir a senha. O aplicativo **não cria usuários** nem concede permissões automaticamente.

## 4. Publicação

Execute `npm run build` para gerar `dist/`. Hospede em Vercel, Netlify ou outro host estático e configure as mesmas variáveis de ambiente `VITE_SUPABASE_URL` e `VITE_SUPABASE_PUBLISHABLE_KEY` no serviço de hospedagem. Configure também os endereços autorizados em Supabase Authentication → URL Configuration, quando aplicável.

## Segurança e limitações desta primeira versão

- RLS precisa permanecer ativo e as políticas precisam ser auditadas antes de uso com dados reais. O aplicativo respeita as políticas do Supabase; não é uma camada de autorização independente.
- A tabela `perfis` encontrada nas capturas utiliza `cargo` (não `funcao`). O dashboard consulta `nome,cargo,ativo`.
- Dashboard calcula métricas a partir dos registros efetivamente cadastrados. Faturamento é estimado pelos campos `data_faturamento` ou status `Faturado`/`Emitido`; requer padronização de estados e conciliação contábil antes de ser usado como relatório oficial.
- O cadastro permite criar e editar registros; não há exclusão na interface. Não inclui ainda uploads de documentos, controle de permissões por obra, relatórios PDF, aprovação de compras, fluxo de caixa real, conciliação de notas, custo proporcional de alocação, integração de IA ou auditoria de alterações.
- O carregamento inicial está limitado a 1.000 registros por tabela; para operação em escala, implementar paginação e consultas agregadas no banco.
- A instalação e publicação ainda precisam ser realizadas no seu computador/serviço de hospedagem. Nenhuma conexão de produção foi testada por este pacote.
