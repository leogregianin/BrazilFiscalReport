# Contribuindo

Contribuições são bem-vindas! Veja como configurar o projeto para desenvolvimento.

## Configuração do Ambiente de Desenvolvimento

1. Clone o repositório:

    ```bash
    git clone https://github.com/Engenere/BrazilFiscalReport.git
    cd BrazilFiscalReport
    ```

2. Crie um ambiente virtual e instale as dependências:

    ```bash
    python -m venv .venv
    source .venv/bin/activate  # Linux/macOS
    pip install -e '.[dacte,damdfe,cli]'
    pip install pytest pytest-cov ruff
    ```

3. Instale os hooks do pre-commit:

    ```bash
    pip install pre-commit
    pre-commit install
    ```

## Executando Testes

O projeto usa `pytest` para testes. Você também precisará do `qpdf` instalado para testes de comparação de PDF:

```bash
# Instalar qpdf (Ubuntu/Debian)
sudo apt-get install qpdf

# Executar todos os testes
pytest

# Executar com cobertura
pytest --cov=./brazilfiscalreport --cov-branch

# Executar testes para um tipo específico de documento
pytest tests/test_danfe.py
```

## Estilo de Código

O projeto usa [Ruff](https://github.com/astral-sh/ruff) para linting e formatação. Os hooks do pre-commit verificarão automaticamente seu código antes de cada commit.

```bash
# Verificação manual
ruff check .
ruff format .
```

## Regenerando PDFs de Referência

Ao fazer alterações na saída PDF, você pode regenerar os PDFs de referência usados nos testes:

```bash
BFR_GENERATE_EXPECTED=1 pytest tests/test_danfe.py
```

!!! warning
    Só regenere PDFs de referência quando você intencionalmente alterou a saída PDF. Sempre revise a diferença visual antes de fazer o commit.

## Enviando Alterações

1. Faça um fork do repositório
2. Crie uma branch para sua feature (`git checkout -b minha-feature`)
3. Faça commit das suas alterações
4. Faça push para seu fork e abra um Pull Request

Certifique-se de que todos os testes passam e os hooks do pre-commit estão limpos antes de enviar.
