# Arquitetura: Consulta Reforma

Visão de alto nível, limitada ao que o produto já mostra publicamente em [consultareforma.tec.br](https://consultareforma.tec.br/).

## Fluxo da consulta

```mermaid
flowchart TB
    A[Usuário cola um ou mais CNPJs] --> B[Informa e-mail e aceita os termos]
    B --> C[Consulta na base pública da Receita]
    C --> D[Situação cadastral]
    C --> E[Simples Nacional e MEI]
    C --> F[Regime declarado]
    C --> G[Certidão federal - planos pagos]
    D --> H{Regra geral da Reforma}
    E --> H
    F --> H
    G --> H
    H --> I[Parecer: gera crédito, em risco ou não gera]
    I --> J[Crédito estimado com CBS de 2027]
    J --> K[Resultado na tela e relatório PDF]
```

## Regra de classificação

| Situação do fornecedor | Resultado |
|---|---|
| Fora do Simples, CNPJ ativo, certidão em dia | Gera crédito |
| Fora do Simples, sem certidão emitida | Crédito em risco |
| Simples Nacional, MEI, pessoa física ou CNPJ irregular | Não gera crédito integral |

## O que é regra e o que é IA

A classificação é **regra**, não IA: segue a regra geral da Reforma (Emenda Constitucional 132/2023 e Lei Complementar 214/2025) sobre dados públicos da Receita Federal.

## Acompanhamento

Nos planos pagos, os fornecedores da carteira são verificados todo mês (certidão e status), e o usuário recebe alerta por e-mail quando algo muda.
