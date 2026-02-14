[![tests](https://github.com/engenere/BrazilFiscalReport/workflows/tests/badge.svg)](https://github.com/Engenere/BrazilFiscalReport/actions)
[![codecov](https://codecov.io/gh/engenere/BrazilFiscalReport/branch/main/graph/badge.svg)](https://app.codecov.io/gh/Engenere/BrazilFiscalReport)
[![python](https://img.shields.io/github/languages/top/Engenere/brazilfiscalreport)](https://pypi.org/project/BrazilFiscalReport/)
[![pypi](https://img.shields.io/pypi/v/brazilfiscalreport.svg)](https://pypi.org/project/BrazilFiscalReport/)
[![license](https://img.shields.io/github/license/Engenere/BrazilFiscalReport)](https://github.com/Engenere/BrazilFiscalReport/blob/main/LICENSE)
[![contributors](https://img.shields.io/github/contributors/Engenere/BrazilFiscalReport)](https://github.com/Engenere/BrazilFiscalReport/graphs/contributors)

[![pypi-downloads](https://static.pepy.tech/badge/brazilfiscalreport)](https://pepy.tech/projects/brazilfiscalreport)

# Brazil Fiscal Report

Python library for generating Brazilian auxiliary fiscal documents in PDF from XML documents.

## Supported Documents 📄

- **DANFE** - Documento Auxiliar da Nota Fiscal Eletrônica (NF-e)
- **DACCe** - Documento Auxiliar da Carta de Correção Eletrônica (CC-e)
- **DACTE** - Documento Auxiliar do Conhecimento de Transporte Eletrônico (CT-e)
- **DAMDFE** - Documento Auxiliar do Manifesto Eletrônico de Documentos Fiscais (MDF-e)

Check the [documentation](https://engenere.github.io/BrazilFiscalReport/) for more ✨✨✨

## Dependencies 🛠️

- [FPDF2](https://github.com/py-pdf/fpdf2) - PDF creation library for Python
- phonenumbers
- python-barcode
- qrcode (required for DACTE and DAMDFE)

## To install 🔧

```bash
pip install brazilfiscalreport
```

## Installing DACTE with Dependencies
If you specifically need the DACTE functionality, you can install it along with its required dependencies using:

```bash
pip install 'brazilfiscalreport[dacte]'
```

## Installing DAMDFE with Dependencies
If you specifically need the DAMDFE functionality, you can install it along with its required dependencies using:

```bash
pip install 'brazilfiscalreport[damdfe]'
```

### Installing CLI with Dependencies
If you specifically need the CLI functionality, you can install it along with its required dependencies using:

```bash
pip install 'brazilfiscalreport[cli]'
```

## Credits 🙌
This is a fork of the [nfe_utils](https://github.com/edsonbernar/nfe_utils) project, originally created by [Edson Bernardino](https://github.com/edsonbernar).

## Maintainer 🛠️
[![Engenere](https://storage.googleapis.com/eng-imagens/logo-fundo-preto.webp)]([#](https://engenere.one/))
