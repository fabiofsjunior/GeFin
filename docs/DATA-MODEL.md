# Modelo de dados — proposta inicial

Entidades: users (firebase_uid único), accounts, categories, transactions, transaction_sources, cards, card_statements, installments, budgets, recurring_incomes, imports, import_rows, chat_threads, chat_messages, ai_proposals, open_finance_connections, consents, outbox_events, sync_checkpoints, audit_events.

## Invariantes
- PK UUID; owner_uid obrigatório em todo registro privado; FKs e índices compostos por owner_uid.
- Valores financeiros como BIGINT de centavos, currency ISO 4217, timezone explícito; timestamps UTC, data de competência separada da data de criação.
- transaction: direction (income/expense/transfer), status, amount_minor, occurred_at, description, category_id, account_id, card_id opcional, source, external_id opcional, version.
- Não misturar pagamento de fatura com compra: pagamento é liquidação/transferência e não uma nova despesa de consumo; definir regra de caixa vs competência nos relatórios.
- Chave única de idempotência por owner_uid + origem + request_key; unique externo por provider+connection+external_id quando confiável; fingerprint é heurística, não substitui identificador.
- Importações: hash de arquivo, hash de linha normalizada, estado staged/approved/rejected/committed, associação a transaction_id; transação confirmada apenas após commit.
- Exclusão: soft delete/tombstone para sincronização e auditoria; retenção conforme política de privacidade.
- Row Level Security por usuário onde houver acesso de cliente ao Supabase; se apenas backend acessar, autorização obrigatória no servidor e RLS como defesa adicional. Firebase UID não deve ser tratado como claim JWT Supabase automaticamente sem integração explícita e verificada.
- Replicação: outbox imutável, seq monotônica por stream ou cursor durável, inbox de eventos aplicados e verificação de divergências.
