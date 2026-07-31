# Diccionario de datos

Fuente: **Online Retail**, UCI Machine Learning Repository.

| Campo | Significado |
|---|---|
| `InvoiceNo` | Identificador de la factura o transacción. Los códigos iniciados con `C` indican cancelación según la documentación de UCI. |
| `StockCode` | Código identificador del producto. |
| `Description` | Descripción del producto. |
| `Quantity` | Cantidad del producto registrada en esa línea. |
| `InvoiceDate` | Fecha y hora de creación de la transacción. |
| `UnitPrice` | Precio unitario en libras esterlinas. |
| `CustomerID` | Identificador del cliente cuando está disponible. |
| `Country` | País de residencia registrado para el cliente. |

## Granularidad esperada

Una fila representa una **línea de producto dentro de una factura**, no necesariamente una factura completa. Esta interpretación debe comprobarse durante el reconocimiento inicial.

## Campos derivados previstos

Estos campos no existen en el archivo original y solo se crearán después de validar las reglas:

| Campo | Propósito |
|---|---|
| `line_value` | `Quantity * UnitPrice`. |
| `transaction_type` | Separar venta completada y cancelación. |
| `year_month` | Agrupación mensual reproducible. |

No crear campos derivados antes de revisar cantidades, precios, invoices y fechas.
