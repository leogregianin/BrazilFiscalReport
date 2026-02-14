Generate DANFE, DACCe, DACTE, and DAMDFE documents directly from the terminal.
The PDF will be saved in the current directory, and you can create
a `config.yaml` file with issuer details and other configurations.

## Installation

The CLI requires additional dependencies. Install them with:

```bash
pip install 'brazilfiscalreport[cli]'
```

## Version

Use the `--version` or `-v` option to check the installed version:

```bash
bfrep --version
```

## Commands

### DANFE

```bash
bfrep danfe /path/to/nfe.xml
```

### DACCe

```bash
bfrep dacce /path/to/cce.xml
```

### DACTE

```bash
bfrep dacte /path/to/cte.xml
```

### DAMDFE

```bash
bfrep damdfe /path/to/mdfe.xml
```

## Configuration File ⚙️

Create a `config.yaml` file in the directory where you run the command. This file allows you to configure issuer details, logo, and margins.

#### Example of `config.yaml`

```yaml
ISSUER:
  nome: "EMPRESA LTDA"
  end: "AV. TEST, 100"
  bairro: "CENTRO"
  cep: "01010-000"
  cidade: "SÃO PAULO"
  uf: "SP"
  fone: "(11) 1234-5678"

LOGO: "/path/to/logo.jpg"
TOP_MARGIN: 5.0
RIGHT_MARGIN: 5.0
BOTTOM_MARGIN: 5.0
LEFT_MARGIN: 5.0
```

**Note**: The `ISSUER` section is used only by the `dacce` command. The `LOGO` and margin settings apply to `danfe`, `dacte`, and `damdfe` commands. If no `config.yaml` is found, default values are used.
