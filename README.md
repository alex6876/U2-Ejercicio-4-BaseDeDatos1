# Ejercicio — Base de Datos de Comercio Electrónico y Gestión de Pedidos



Proyecto enfocado en la modelación Entidad-Relación (DER / MER) e implementación de base de datos relacional para una plataforma de comercio electrónico, administrando clientes, direcciones de envío, productos por categoría, pedidos, detalle de ítems comprados y empresas transportistas.

---

## Descripción

El sistema modela una estructura de datos relacional para la gestión integral de ventas en línea y logística de envíos. Permite gestionar las cuentas de usuario y sus múltiples direcciones registradas, el catálogo de productos con su stock y clasificación por categorías, la generación e historial de pedidos concretados, la desgregación de cada compra en renglones o detalles de pedido, y la asignación del transporte responsable de la entrega.

---

## Funcionalidades e Implementación

### Entidades y Atributos

* Cliente:


* id_Cliente: Clave identificadora única del cliente.


* Nombre: Nombre completo del cliente.


* Correo: Dirección de correo electrónico.


* Contraseña: Clave de acceso a la plataforma.


* Dni: Documento Nacional de Identidad.




* Dirección:


* id_Dirección: Clave primaria identificadora de la dirección.


* Calle: Nombre de la calle o vía pública.


* Numero: Altura o número de la vivienda.


* Ciudad: Ciudad o localidad.


* Provincia: Provincia o estado.


* Codigo postal: Código postal de la zona.




* Producto:


* SKU(Pk): Clave primaria identificadora del producto (*Stock Keeping Unit*).


* Codigo: Código identificador de catálogo o barras.


* Nombre: Nombre comercial del producto.


* Descripción: Detalle técnico o descriptivo del producto.


* Precio Unitario: Valor de venta por unidad.


* Stock: Cantidad disponible en inventario.




* Categoria:


* id_Categoria: Clave primaria identificadora de la categoría.


* Nombre: Nombre de la categoría (ej. Electrónica, Indumentaria).




* Pedido:


* Numero de orden(PK): Clave primaria única del pedido.


* Fecha: Fecha de emisión de la compra.


* Hora: Hora de concreción del pedido.


* Monto total: Importe total acumulado del pedido.


* Estado actual: Situación de la orden (ej. pendiente, pagado, despachado).


* id_cliente: Clave foránea referenciando al cliente comprador.


* id_Dirección: Clave foránea que define el destino de entrega.




* Detalle-Pedido:


* Numero de orden(PK): Clave foránea y parte de la clave primaria compuesta que referencia al pedido.


* SKU(Pk): Clave foránea y parte de la clave primaria compuesta que referencia al producto adquirido.


* Cantidad_Solicitada: Número de unidades compradas.


* Precio_Unitario: Precio facturado del producto al momento de la venta.




* Transportista:


* CUIT(PK): Clave primaria única tributaria o identificador del transportista.


* razon_social: Nombre legal o razón social de la empresa logística.


* telefono de atencion: Número telefónico de atención o contacto.


* Numero de guia: Número o código de rastreo del envío asignado.





---

## Relaciones del Modelo

1. Cliente ↔ Dirección (Relación 1:N):


* Un cliente puede registrar múltiples direcciones de entrega, mientras que cada dirección pertenece a un único cliente.




2. Cliente ↔ Pedido (Relación 1:N):


* Un cliente puede realizar múltiples pedidos a lo largo del tiempo, pero cada orden de pedido corresponde a un único cliente.




3. Dirección ↔ Pedido (Relación 1:N):


* Una dirección guardada puede ser seleccionada para el despacho de múltiples pedidos, pero cada pedido tiene asignada una sola dirección de destino.




4. Producto ↔ Categoria (Relación N:1):


* Múltiples productos pertenecen a una misma categoría comercial, pero cada producto se clasifica dentro de una única categoría.




5. Producto ↔ Pedido (Relación N:M):


* Un producto puede formar parte de varios pedidos y un pedido puede incluir varios productos. Esta relación se resuelve operativamente a través de la entidad intermedia `Detalle-Pedido`.




6. Pedido ↔ Detalle-Pedido (Relación 1:N):


* Un pedido contiene uno o más ítems/renglones detallados.




7. Transportista ↔ Pedido / Detalle-Pedido (Relaciones N:1 / 1:N):


* Un transportista se encarga de realizar la entrega logística asignada a los pedidos o sus respectivos ítems de despacho.
