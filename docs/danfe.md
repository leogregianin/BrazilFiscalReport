DANFE (Auxiliary Document of the Electronic Invoice) is a printed representation of the NF-e (Electronic Invoice) used in Brazil. It contains key details about the transaction, such as the seller, buyer, products, and taxes.

## Basic Usage

=== "Python"

    ```python
    from brazilfiscalreport.danfe import Danfe

    # Path to the XML file
    xml_file_path = 'nfe.xml'

    # Load XML Content
    with open(xml_file_path, "r", encoding="utf8") as file:
        xml_content = file.read()

    # Instantiate the DANFE object with the loaded XML content
    danfe = Danfe(xml=xml_content)
    danfe.output('output_danfe.pdf')
    ```

=== "CLI"

    ```bash
    bfrep danfe /path/to/nfe.xml
    ```

## Customizing DANFE 🎨

This section describes how to customize the PDF output of the DANFE using the `DanfeConfig` class. You can adjust various settings such as margins, fonts, and tax configurations according to your needs.

### Configuration Options ⚙️

Here is a breakdown of all the configuration options available in `DanfeConfig`:

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
**Font Size**

- **Type**: `FontSize` (Enum)
- **Values**: `BIG`, `SMALL`
- **Description**: Font size used throughout the PDF document.
- **Example**:
    ```python
    config.font_size = FontSize.BIG
    ```
- **Default**: `SMALL`

---

**Receipt Position**

- **Type**: `ReceiptPosition` (Enum)
- **Values**: `TOP`, `BOTTOM`, `LEFT`
- **Description**: Position of the receipt section in the DANFE.
- **Example**:
    ```python
    config.receipt_pos = ReceiptPosition.BOTTOM
    ```
- **Default**: `TOP` when portrait, `LEFT` when landscape orientation.

!!! note
    In landscape orientation, the receipt position is far left; customization is not permitted.

---

**Decimal Configuration**

- **Type**: `DecimalConfig`
- **Fields**: `price_precision`, `quantity_precision` (both `int`)
- **Description**: Defines the number of decimal places for prices and quantities.
- **Example**:
    ```python
    config.decimal_config = DecimalConfig(price_precision=2, quantity_precision=2)
    ```
- **Default**: `4`

---

**Tax Configuration**

- **Type**: `TaxConfiguration` (Enum)
- **Values**: `STANDARD_ICMS_IPI`, `ICMS_ST`, `WITHOUT_IPI`
- **Description**: Specifies which tax fields to display.
- **Example**:
    ```python
    config.tax_configuration = TaxConfiguration.WITHOUT_IPI
    ```
- **Default**: `STANDARD_ICMS_IPI`

!!! warning
    This feature is not yet implemented.

---

**Invoice Display**

- **Type**: `InvoiceDisplay` (Enum)
- **Values**: `DUPLICATES_ONLY`, `FULL_DETAILS`
- **Description**: Controls the level of detail in the invoice section of the DANFE.
- **Example**:
    ```python
    config.invoice_display = InvoiceDisplay.FULL_DETAILS
    ```
- **Default**: `FULL_DETAILS`

---

**Display PIS COFINS**

- **Type**: `Bool`
- **Values**: `True`, `False`
- **Description**: Whether or not to display PIS and COFINS taxes in the DANFE totals.
- **Example**:
    ```python
    config.display_pis_cofins = True
    ```
- **Default**: `False`

---

**Line break in supplementary information**

- **Type**: `Bool`
- **Values**: `True`, `False`
- **Description**: Break the line using";" in the supplementary information (infCpl) of the DANFE.
- **Example**:
    ```python
    config.infcpl_semicolon_newline= True
    ```
- **Default**: `False`

---

**Product Description Config**

- **Type**: `ProductDescriptionConfig`
- **Fields**: `display_branch` (`bool`), `display_anp` (`bool`), `display_anvisa` (`bool`), `branch_info_prefix` (`str`), `display_additional_info` (`bool`)
- **Description**: Controls what additional information is displayed in the product description column of the DANFE.
- **Example**:
    ```python
    config.product_description_config = ProductDescriptionConfig(
        display_branch=True,
        branch_info_prefix="=>",
        display_additional_info=True,
        display_anp=True,
        display_anvisa=True,
    )
    ```
- **Default**:
    ```python
    ProductDescriptionConfig(
        display_branch=False,
        display_anp=False,
        display_anvisa=False,
        branch_info_prefix="",
        display_additional_info=True,
    )
    ```

---

**Watermark Cancelled**

- **Type**: `bool`
- **Description**: When set to `True`, displays a "CANCELADA" watermark on the DANFE for cancelled invoices. For XML files without the `protNFe` tag, a "SEM VALOR FISCAL" watermark is displayed regardless of this setting.
- **Example**:
    ```python
    config.watermark_cancelled = True
    ```
- **Default**: `False`

---

### Usage Example with Customization

Here’s how to set up a ``DanfeConfig`` object with a full set of customizations::

```python
from brazilfiscalreport.danfe import (
    Danfe,
    DanfeConfig,
    DecimalConfig,
    FontType,
    InvoiceDisplay,
    Margins,
    ProductDescriptionConfig,
    ReceiptPosition,
    TaxConfiguration,
)

# Path to the XML file
xml_file_path = 'nfe.xml'

# Load XML Content
with open(xml_file_path, "r", encoding="utf8") as file:
    xml_content = file.read()

# Create a configuration instance
config = DanfeConfig(
    logo='path/to/logo.png',
    margins=Margins(top=10, right=10, bottom=10, left=10),
    receipt_pos=ReceiptPosition.BOTTOM,
    decimal_config=DecimalConfig(price_precision=2, quantity_precision=2),
    tax_configuration=TaxConfiguration.ICMS_ST,
    invoice_display=InvoiceDisplay.FULL_DETAILS,
    font_type=FontType.TIMES,
    display_pis_cofins=True,
    product_description_config=ProductDescriptionConfig(
        display_branch=True,
        display_additional_info=True,
    ),
)

# Use this config when creating a Danfe instance
danfe = Danfe(xml_content, config=config)
danfe.output('output_danfe.pdf')
```
