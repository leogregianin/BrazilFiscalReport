DACTE (Auxiliary Document of the Electronic Transportation Bill) is a printed document used in Brazil to accompany the electronic transportation invoice (CT-e). It serves as a simplified version of the CT-e, providing key details about the shipment, such as cargo information, sender and receiver, and transport company data.

## Basic Usage

=== "Python"

    ```python
    from brazilfiscalreport.dacte import Dacte

    # Path to the XML file
    xml_file_path = 'cte.xml'

    # Load XML Content
    with open(xml_file_path, "r", encoding="utf8") as file:
        xml_content = file.read()

    # Instantiate the DACTE object with the loaded XML content
    dacte = Dacte(xml=xml_content)
    dacte.output('output_dacte.pdf')
    ```

=== "CLI"

    ```bash
    bfrep dacte /path/to/cte.xml
    ```

## Customizing DACTE 🎨

This section describes how to customize the PDF output of the DACTE using the `DacteConfig` class. You can adjust various settings such as margins, fonts, and other options according to your needs.

### Configuration Options ⚙️

Here is a breakdown of all the configuration options available in `DacteConfig`:

---

**Logo**

- **Type**: `str`, `BytesIO`, or `bytes`
- **Description**: Path to the logo file or binary image data to be included in the PDF. You can use a file path string or pass image data directly.
- **Example**:
    ```python
    config.logo = "path/to/logo.jpg"  # Using a file path
    ```
- **Default**: No logo.

---

**Margins**

- **Type**: `Margins`
- **Fields**: `top`, `right`, `bottom`, `left` (all of type `Number`)
- **Description**: Sets the page margins for the PDF document.
- **Example**:
    ```python
    config.margins = Margins(top=5, right=5, bottom=5, left=5)
    ```
- **Default**: top, right, bottom, and left are set to 5 mm.

---

**Receipt Position**

- **Type**: `ReceiptPosition` (Enum)
- **Values**: `TOP`, `BOTTOM`, `LEFT`
- **Description**: Position of the receipt section in the DACTE.
- **Example**:
    ```python
    config.receipt_pos = ReceiptPosition.BOTTOM
    ```
- **Default**: `TOP`

---

**Decimal Configuration**

- **Type**: `DecimalConfig`
- **Fields**: `price_precision`, `quantity_precision` (both `int`)
- **Description**: Defines the number of decimal places for prices and quantities.
- **Example**:
    ```python
    config.decimal_config = DecimalConfig(price_precision=2, quantity_precision=2)
    ```
- **Default**: `4` for both fields.

---

**Font Type**

- **Type**: `FontType` (Enum)
- **Values**: `COURIER`, `TIMES`
- **Description**: Font style used throughout the PDF document.
- **Example**:
    ```python
    config.font_type = FontType.COURIER
    ```
- **Default**: `TIMES`

---

**Watermark Cancelled**

- **Type**: `bool`
- **Description**: When set to `True`, displays a "CANCELADA" watermark on the DACTE for cancelled documents.
- **Example**:
    ```python
    config.watermark_cancelled = True
    ```
- **Default**: `False`

---

### Usage Example with Customization

Here's how to set up a DacteConfig object with a full set of customizations:

```python
from brazilfiscalreport.dacte import (
    Dacte,
    DacteConfig,
    DecimalConfig,
    FontType,
    Margins,
    ReceiptPosition,
)

# Path to the XML file
xml_file_path = 'cte.xml'

# Load XML Content
with open(xml_file_path, "r", encoding="utf8") as file:
    xml_content = file.read()

# Create a configuration instance
config = DacteConfig(
    logo='path/to/logo.png',
    margins=Margins(top=10, right=10, bottom=10, left=10),
    receipt_pos=ReceiptPosition.BOTTOM,
    decimal_config=DecimalConfig(price_precision=2, quantity_precision=2),
    font_type=FontType.TIMES,
)

# Use this config when creating a Dacte instance
dacte = Dacte(xml_content, config=config)
dacte.output('output_dacte.pdf')
```
