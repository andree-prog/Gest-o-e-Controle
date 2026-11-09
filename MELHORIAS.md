# Gestão e Controle — melhoria 01 (segura)

Esta versão mantém o banco e as tabelas existentes.

## Ajustes implementados
- Ao editar um cadastro, campos opcionais apagados passam a ser enviados como `null`, permitindo limpar valores anteriores.
- A verificação de obras atrasadas usa a data local do navegador, em vez de UTC.

## Limitações atuais
- Financeiro ainda não distingue obrigação, custo e pagamento.
- Pedidos e notas não possuem vínculo formal com lançamento financeiro.
- É necessário verificar as políticas RLS do Supabase antes de liberar múltiplos usuários.
- Não foram aplicadas migrações de banco de dados.

## Publicação segura
1. Crie uma branch no GitHub (ex.: `melhoria-01`) e envie os arquivos desta pasta.
2. Revise a prévia da Vercel e teste edição/limpeza de campo em dados fictícios.
3. Faça backup do Supabase antes de qualquer futura migração.
4. Só depois de validar, integre à branch principal.

Não envie arquivos `.env` com credenciais. Configure `VITE_SUPABASE_URL` e `VITE_SUPABASE_PUBLISHABLE_KEY` na Vercel.
