# valo-cicd-contracts

Repositorio canonical dos schemas e templates do Contrato Operacional de CI/CD da Valo Technology (JELP).

## Estrutura

```
valo-cicd-contracts/
├── schemas/meta.schema.json            # JSON Schema draft-07
├── examples/
│   ├── meta-t1-low.example.json
│   ├── meta-t2-medium.example.json
│   └── meta-t2-high.example.json
├── templates/PULL_REQUEST_TEMPLATE.md  # Template de PR
├── workflows/cicd-contract-lint.yml    # GitHub Action de validacao
└── README.md
```

## Consumo em outros repos

### Opcao 1 — Raw URL (recomendado)

Baixe o schema diretamente no workflow:

```yaml
- name: Download schema
  run: |
    curl -fsSL https://raw.githubusercontent.com/RenoirBagi/valo-cicd-contracts/master/schemas/meta.schema.json \
      -o /tmp/meta.schema.json
    npx ajv-cli validate -s /tmp/meta.schema.json -d /tmp/meta.json --strict=false
```

### Opcao 2 — Submodule

```bash
git submodule add https://github.com/RenoirBagi/valo-cicd-contracts.git .github/cicd-contracts
```

Referencia no workflow:

```yaml
- uses: actions/checkout@v4
  with:
    submodules: true
- run: npx ajv-cli validate -s .github/cicd-contracts/schemas/meta.schema.json -d /tmp/meta.json
```

### Opcao 3 — Copia manual

```bash
mkdir -p .github/schemas
curl -fsSL https://raw.githubusercontent.com/RenoirBagi/valo-cicd-contracts/master/schemas/meta.schema.json \
  -o .github/schemas/meta.schema.json
```

## Validacao local

```bash
npx ajv-cli validate -s schemas/meta.schema.json -d examples/meta-t1-low.example.json --strict=false
```

## Tracks

| Track | Criterio | Aprovacao |
|-------|----------|-----------|
| T1 Low | copy, CSS, doc | Renoir (auto-merge se CI verde) |
| T2 Medium | nova feature, edge function, RLS adicional | Renoir ou Guilherme |
| T2 High | migration, RLS existente, billing | Renoir e Guilherme |
| T3 | secrets, integracao externa | Renoir + runbook |
| T4 | refactor critico, auth, motor financeiro | Renoir + release controlado |

## Branches

- `master` — versao estavel
- `dev` — desenvolvimento

Contrato completo: [principles_cicd_pipeline.md](https://github.com/RenoirBagi/valo-cicd-contracts/blob/master/docs/principles_cicd_pipeline.md) (a ser migrado).
