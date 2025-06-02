
Generate DACTE, DANFE, and DACCE documents directly from the terminal. The PDF will be saved in the current directory, and you'll need to create a config.yaml file with issuer details and other configurations.

Use the --version or -v option to check the installed version.

#### Example of `config.yaml` ⚙️

```yaml
ISSUER:
  name: "EMPRESA LTDA"
  address: "AV. TEST, 100"
  city: "SÃO PAULO"
  state: "SP"
  phone: "(11) 1234-5678"

LOGO: "/path/to/logo.jpg"
TOP_MARGIN: 5.0
RIGHT_MARGIN: 5.0
BOTTOM_MARGIN: 5.0
LEFT_MARGIN: 5.0
```
