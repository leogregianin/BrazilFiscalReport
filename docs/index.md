[![image](https://github.com/engenere/BrazilFiscalReport/workflows/tests/badge.svg)](https://github.com/Engenere/BrazilFiscalReport/actions)
[![image](https://codecov.io/gh/engenere/BrazilFiscalReport/branch/main/graph/badge.svg)](https://app.codecov.io/gh/Engenere/BrazilFiscalReport)
[![image](https://img.shields.io/github/languages/top/Engenere/brazilfiscalreport)](https://pypi.org/project/BrazilFiscalReport/)
[![image](https://img.shields.io/pypi/v/brazilfiscalreport.svg)](https://pypi.org/project/BrazilFiscalReport/)
[![image](https://img.shields.io/pypi/l/brazilfiscalreport)](https://github.com/Engenere/BrazilFiscalReport/blob/main/LICENSE)


# Brazil Fiscal Report

![Brazil Fiscal Report - XML to PDF](assets/banner.svg)

Python library for generating Brazilian auxiliary fiscal documents in PDF from XML documents.

## Supported Documents

| Document | Description | XML Source |
|----------|-------------|------------|
| [**DANFE**](danfe.md) | Documento Auxiliar da Nota Fiscal Eletrônica | NF-e |
| [**DACCe**](dacce.md) | Documento Auxiliar da Carta de Correção Eletrônica | CC-e |
| [**DACTE**](dacte.md) | Documento Auxiliar do Conhecimento de Transporte Eletrônico | CT-e |
| [**DAMDFE**](damdfe.md) | Documento Auxiliar do Manifesto Eletrônico de Documentos Fiscais | MDF-e |

## Usage Modes

### 1. Python Code

For full customization and integration, use the library directly in Python. Configure margins, fonts, receipt positions, and more for each document type.

[Get started :material-arrow-right:](getting-started.md){ .md-button }

### 2. CLI (Command Line)

For quick PDF generation from the terminal with a simple `config.yaml` file.

[CLI documentation :material-arrow-right:](cli.md){ .md-button }

### 3. Try it Online

Upload your fiscal XML and get the PDF instantly — no installation needed.

[Try it online :material-arrow-right:](https://brazilfiscalreport.streamlit.app){ .md-button }

## Dependencies

- [FPDF2](https://github.com/py-pdf/fpdf2) - PDF creation library for Python
- [phonenumbers](https://github.com/daviddrysdale/python-phonenumbers) - Phone number formatting
- [python-barcode](https://github.com/WhyNotHugo/python-barcode) - Barcode generation
- [qrcode](https://github.com/lincolnloop/python-qrcode) - QR code generation (required for DACTE and DAMDFE)
