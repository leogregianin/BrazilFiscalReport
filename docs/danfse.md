DANFSE (Auxiliary Document of the Electronic Service Invoice) is a printed document used in Brazil to accompany the electronic service invoice (NFS-e). It serves as a simplified version of the NFS-e, providing key details about the service provided, such as issuer and taker information, tax details, and total amounts.

## Basic Usage

=== "Python"

    ```python
    from brazilfiscalreport.danfse import Danfse

    # Path to the XML file
    xml_file_path = 'nfse.xml'

    # Load XML Content
    with open(xml_file_path, "r", encoding="utf8") as file:
        xml_content = file.read()

    # Instantiate the DANFSE object with the loaded XML content
    danfse = Danfse(xml=xml_content)
    danfse.output('output_danfse.pdf')
    ```

=== "CLI"

    ```bash
    bfrep danfse /path/to/nfse.xml
    ```

## Customizing DANFSE

This section describes how to customize the PDF output of the DANFSE using the `DanfseConfig` class. You can adjust various settings such as margins and fonts according to your needs.

### Margins

You can customize the margins of the PDF output by providing a `Margins` object.

```python
from brazilfiscalreport.danfse import Danfse, DanfseConfig, Margins

config = DanfseConfig(
    margins=Margins(top=5, right=5, bottom=5, left=5)
)

danfse = Danfse(xml=xml_content, config=config)
danfse.output('output_danfse.pdf')
```

### Cancelled Watermark

To display a "CANCELADA" watermark on cancelled documents:

```python
from brazilfiscalreport.danfse import Danfse, DanfseConfig

config = DanfseConfig(watermark_cancelled=True)

danfse = Danfse(xml=xml_content, config=config)
danfse.output('output_danfse.pdf')
```
