[![image](https://github.com/engenere/BrazilFiscalReport/workflows/tests/badge.svg)](https://github.com/Engenere/BrazilFiscalReport/actions)
[![image](https://codecov.io/gh/engenere/BrazilFiscalReport/branch/main/graph/badge.svg)](https://app.codecov.io/gh/Engenere/BrazilFiscalReport)
[![image](https://img.shields.io/github/languages/top/Engenere/brazilfiscalreport)](https://pypi.org/project/BrazilFiscalReport/)
[![image](https://img.shields.io/pypi/v/brazilfiscalreport.svg)](https://pypi.org/project/BrazilFiscalReport/)
[![image](https://img.shields.io/pypi/l/brazilfiscalreport)](https://github.com/Engenere/BrazilFiscalReport/blob/main/LICENSE)


# Brazil Fiscal Report

Biblioteca Python para geração de documentos fiscais auxiliares brasileiros em PDF a partir de documentos XML.

## Documentos Suportados

| Documento | Descrição | Origem XML |
|-----------|-----------|------------|
| [**DANFE**](danfe.md) | Documento Auxiliar da Nota Fiscal Eletrônica | NF-e |
| [**DACCe**](dacce.md) | Documento Auxiliar da Carta de Correção Eletrônica | CC-e |
| [**DACTE**](dacte.md) | Documento Auxiliar do Conhecimento de Transporte Eletrônico | CT-e |
| [**DAMDFE**](damdfe.md) | Documento Auxiliar do Manifesto Eletrônico de Documentos Fiscais | MDF-e |

## Modos de Uso

### 1. Código Python

Para personalização completa e integração, use a biblioteca diretamente em Python. Configure margens, fontes, posição do recibo e muito mais para cada tipo de documento.

[Começar :material-arrow-right:](getting-started.md){ .md-button }

### 2. CLI (Linha de Comando)

Para geração rápida de PDF pelo terminal com um simples arquivo `config.yaml`.

[Documentação do CLI :material-arrow-right:](cli.md){ .md-button }

## Dependências

- [FPDF2](https://github.com/py-pdf/fpdf2) - Biblioteca de criação de PDF para Python
- [phonenumbers](https://github.com/daviddrysdale/python-phonenumbers) - Formatação de números de telefone
- [python-barcode](https://github.com/WhyNotHugo/python-barcode) - Geração de código de barras
- [qrcode](https://github.com/lincolnloop/python-qrcode) - Geração de QR code (necessário para DACTE e DAMDFE)
