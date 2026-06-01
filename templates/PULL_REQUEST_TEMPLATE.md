## Resumo

<!-- Descreva o que esse PR faz em 2-3 frases -->

## Track e Risk

Marque o track conforme o Contrato CI/CD JELP:

- [ ] **T1 Low** — copy, CSS isolado, doc
- [ ] **T2 Medium** — nova feature UI, edge function, RLS adicional
- [ ] **T2 High** — migration Supabase, mudanca RLS existente, billing
- [ ] **T3** — secrets, integracao externa, DNS
- [ ] **T4** — refactor critico, auth, motor financeiro

## meta.json

```json
{
  "id": "YYYYMMDD-HHMM-<projeto>-<topic-kebab>",
  "project": "luminis",
  "track": "T1",
  "risk": "low",
  "scope": ["frontend"],
  "tables_affected": [],
  "rls_changed": false,
  "fiscal_impact": false,
  "billing_impact": false,
  "expected_rows_migration": 0,
  "preview_url_required": true,
  "verify_steps": ["..."],
  "rollback_strategy": "...",
  "approvers": ["renoir"],
  "co_approvers_allowed": ["guilherme"],
  "evidence": []
}
```

## Verify Steps

<!-- Copie os verify_steps do meta.json aqui para facilitar checklist de revisao -->
- [ ] ...

## Rollback Strategy

<!-- Descreva como reverter se algo der errado -->

## Evidencia

<!-- Anexe screenshots, logs, links de preview conforme o track exigir -->

---
Schema: [meta.schema.json](https://raw.githubusercontent.com/RenoirBagi/valo-cicd-contracts/master/schemas/meta.schema.json)
Contrato completo: [Documentacao CI/CD JELP](https://github.com/RenoirBagi/valo-cicd-contracts/blob/master/README.md)
