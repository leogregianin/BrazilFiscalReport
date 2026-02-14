Gere documentos DANFE, DACCe, DACTE e DAMDFE diretamente pelo terminal.
O PDF será salvo no diretório atual, e você pode criar
um arquivo `config.yaml` com detalhes do emitente e outras configurações.

## Instalação

O CLI requer dependências adicionais. Instale-as com:

```bash
pip install 'brazilfiscalreport[cli]'
```

## Versão

Use a opção `--version` ou `-v` para verificar a versão instalada:

```bash
bfrep --version
```

## Comandos

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

## Arquivo de Configuração ⚙️

Crie um arquivo `config.yaml` no diretório onde você executa o comando. Este arquivo permite configurar detalhes do emitente, logo e margens.

#### Exemplo de `config.yaml`

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

**Nota**: A seção `ISSUER` é usada apenas pelo comando `dacce`. As configurações de `LOGO` e margens se aplicam aos comandos `danfe`, `dacte` e `damdfe`. Se nenhum `config.yaml` for encontrado, os valores padrão serão utilizados.
