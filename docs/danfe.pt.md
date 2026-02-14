DANFE (Documento Auxiliar da Nota Fiscal Eletrônica) é uma representação impressa da NF-e (Nota Fiscal Eletrônica) usada no Brasil. Contém os principais detalhes da transação, como vendedor, comprador, produtos e impostos.

## Uso Básico

=== "Python"

    ```python
    from brazilfiscalreport.danfe import Danfe

    # Caminho para o arquivo XML
    xml_file_path = 'nfe.xml'

    # Carregar conteúdo do XML
    with open(xml_file_path, "r", encoding="utf8") as file:
        xml_content = file.read()

    # Instanciar o objeto DANFE com o conteúdo XML carregado
    danfe = Danfe(xml=xml_content)
    danfe.output('output_danfe.pdf')
    ```

=== "CLI"

    ```bash
    bfrep danfe /path/to/nfe.xml
    ```

## Personalizando o DANFE 🎨

Esta seção descreve como personalizar a saída PDF do DANFE usando a classe `DanfeConfig`. Você pode ajustar diversas configurações como margens, fontes e configurações de impostos de acordo com suas necessidades.

### Opções de Configuração ⚙️

Aqui está uma descrição de todas as opções de configuração disponíveis em `DanfeConfig`:

---

**Logo**

- **Tipo**: `str`, `BytesIO` ou `bytes`
- **Descrição**: Caminho para o arquivo de logo ou dados binários da imagem a ser incluída no PDF. Você pode usar uma string com o caminho do arquivo ou passar os dados da imagem diretamente.
- **Exemplo**:
    ```python
    config.logo = "path/to/logo.jpg"  # Usando caminho do arquivo
    ```
- **Padrão**: Sem logo.

---

**Margens**

- **Tipo**: `Margins`
- **Campos**: `top`, `right`, `bottom`, `left` (todos do tipo `Number`)
- **Descrição**: Define as margens da página do documento PDF.
- **Exemplo**:
    ```python
    config.margins = Margins(top=5, right=5, bottom=5, left=5)
    ```
- **Padrão**: top, right, bottom e left definidos como 5 mm.

---

**Tipo de Fonte**

- **Tipo**: `FontType` (Enum)
- **Valores**: `COURIER`, `TIMES`
- **Descrição**: Estilo de fonte usado em todo o documento PDF.
- **Exemplo**:
    ```python
    config.font_type = FontType.COURIER
    ```
- **Padrão**: `TIMES`

---
**Tamanho da Fonte**

- **Tipo**: `FontSize` (Enum)
- **Valores**: `BIG`, `SMALL`
- **Descrição**: Tamanho da fonte usado em todo o documento PDF.
- **Exemplo**:
    ```python
    config.font_size = FontSize.BIG
    ```
- **Padrão**: `SMALL`

---

**Posição do Recibo**

- **Tipo**: `ReceiptPosition` (Enum)
- **Valores**: `TOP`, `BOTTOM`, `LEFT`
- **Descrição**: Posição da seção de recibo no DANFE.
- **Exemplo**:
    ```python
    config.receipt_pos = ReceiptPosition.BOTTOM
    ```
- **Padrão**: `TOP` quando retrato, `LEFT` quando orientação paisagem.

!!! note
    Na orientação paisagem, a posição do recibo é no lado esquerdo; personalização não é permitida.

---

**Configuração Decimal**

- **Tipo**: `DecimalConfig`
- **Campos**: `price_precision`, `quantity_precision` (ambos `int`)
- **Descrição**: Define o número de casas decimais para preços e quantidades.
- **Exemplo**:
    ```python
    config.decimal_config = DecimalConfig(price_precision=2, quantity_precision=2)
    ```
- **Padrão**: `4`

---

**Configuração de Impostos**

- **Tipo**: `TaxConfiguration` (Enum)
- **Valores**: `STANDARD_ICMS_IPI`, `ICMS_ST`, `WITHOUT_IPI`
- **Descrição**: Especifica quais campos de impostos exibir.
- **Exemplo**:
    ```python
    config.tax_configuration = TaxConfiguration.WITHOUT_IPI
    ```
- **Padrão**: `STANDARD_ICMS_IPI`

!!! warning
    Este recurso ainda não foi implementado.

---

**Exibição da Fatura**

- **Tipo**: `InvoiceDisplay` (Enum)
- **Valores**: `DUPLICATES_ONLY`, `FULL_DETAILS`
- **Descrição**: Controla o nível de detalhe na seção de fatura do DANFE.
- **Exemplo**:
    ```python
    config.invoice_display = InvoiceDisplay.FULL_DETAILS
    ```
- **Padrão**: `FULL_DETAILS`

---

**Exibir PIS COFINS**

- **Tipo**: `Bool`
- **Valores**: `True`, `False`
- **Descrição**: Define se os impostos PIS e COFINS devem ser exibidos nos totais do DANFE.
- **Exemplo**:
    ```python
    config.display_pis_cofins = True
    ```
- **Padrão**: `False`

---

**Configuração da Descrição do Produto**

- **Tipo**: `ProductDescriptionConfig`
- **Campos**: `display_branch` (`bool`), `display_anp` (`bool`), `display_anvisa` (`bool`), `branch_info_prefix` (`str`), `display_additional_info` (`bool`)
- **Descrição**: Controla quais informações adicionais são exibidas na coluna de descrição do produto do DANFE.
- **Exemplo**:
    ```python
    config.product_description_config = ProductDescriptionConfig(
        display_branch=True,
        branch_info_prefix="=>",
        display_additional_info=True,
        display_anp=True,
        display_anvisa=True,
    )
    ```
- **Padrão**:
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

**Marca d'água Cancelada**

- **Tipo**: `bool`
- **Descrição**: Quando definido como `True`, exibe uma marca d'água "CANCELADA" no DANFE para notas fiscais canceladas. Para arquivos XML sem a tag `protNFe`, uma marca d'água "SEM VALOR FISCAL" é exibida independentemente desta configuração.
- **Exemplo**:
    ```python
    config.watermark_cancelled = True
    ```
- **Padrão**: `False`

---

### Exemplo de Uso com Personalização

Veja como configurar um objeto ``DanfeConfig`` com um conjunto completo de personalizações::

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

# Caminho para o arquivo XML
xml_file_path = 'nfe.xml'

# Carregar conteúdo do XML
with open(xml_file_path, "r", encoding="utf8") as file:
    xml_content = file.read()

# Criar uma instância de configuração
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

# Usar esta configuração ao criar uma instância do Danfe
danfe = Danfe(xml_content, config=config)
danfe.output('output_danfe.pdf')
```
