# Getting Started

## Installation

### Basic installation

```bash
pip install brazilfiscalreport
```

This installs the core library with support for **DANFE** and **DACCe**.

### Optional dependencies

Some document types require additional packages:

=== "DACTE"

    ```bash
    pip install 'brazilfiscalreport[dacte]'
    ```

=== "DAMDFE"

    ```bash
    pip install 'brazilfiscalreport[damdfe]'
    ```

=== "CLI"

    ```bash
    pip install 'brazilfiscalreport[cli]'
    ```

=== "All extras"

    ```bash
    pip install 'brazilfiscalreport[dacte,damdfe,cli]'
    ```

## Quick Start

### Using Python code

Generate a DANFE PDF from an NF-e XML file in just a few lines:

```python
from brazilfiscalreport.danfe import Danfe

# Load the XML content
with open("nfe.xml", "r", encoding="utf8") as file:
    xml_content = file.read()

# Generate the PDF
danfe = Danfe(xml=xml_content)
danfe.output("danfe.pdf")
```

The same pattern applies to all document types:

=== "DANFE"

    ```python
    from brazilfiscalreport.danfe import Danfe

    danfe = Danfe(xml=xml_content)
    danfe.output("danfe.pdf")
    ```

=== "DACCe"

    ```python
    from brazilfiscalreport.dacce import DaCCe

    dacce = DaCCe(xml=xml_content)
    dacce.output("dacce.pdf")
    ```

=== "DACTE"

    ```python
    from brazilfiscalreport.dacte import Dacte

    dacte = Dacte(xml=xml_content)
    dacte.output("dacte.pdf")
    ```

=== "DAMDFE"

    ```python
    from brazilfiscalreport.damdfe import Damdfe

    damdfe = Damdfe(xml=xml_content)
    damdfe.output("damdfe.pdf")
    ```

### Using the CLI

For quick generation from the terminal:

```bash
bfrep danfe /path/to/nfe.xml
bfrep dacce /path/to/cce.xml
bfrep dacte /path/to/cte.xml
bfrep damdfe /path/to/mdfe.xml
```

See the [CLI documentation](cli.md) for configuration options.

## Next steps

- Learn about customization options for each document type: [DANFE](danfe.md), [DACTE](dacte.md), [DAMDFE](damdfe.md), [DACCe](dacce.md)
- Configure the [CLI](cli.md) for batch generation
