###################################################################################################
Unidades de medida
###################################################################################################

Esta funcionalidad permite administrar unidades de medida diferente entre entre las compras y las ventas.

Un ejemplo en el caso de nuestra empresa ficticia Computotal que compra los DVD's virgen en paquetes 
de 100 unidades y los vende por unidades individuales.

Veamos con un ejemplo los pasos a seguir en estos casos.

*************************************************
Configuración
*************************************************

Para habilitar la funcionalidad debemos acceder a Inventario/Configuración/Ajustes/Productos:

.. image:: media/unidad-medida-1.png
   :align: center
   :scale: 75 %

Después de activar la funcionalidad, se muestran dos opciones de menú nuevas:

.. image:: media/unidad-medida-3.png
   :align: center
   :scale: 75 %

Una de las opciones permite admnistrar las categorías en las que se pueden clasificar las unidades de medida.

.. image:: media/unidad-medida-4.png
   :align: center
   :scale: 75 %

La otra opción, permite gestionar las unidades de medida en Odoo.

Vamos a crear una agrupación personalizada por Categorías para poder analizarlas mejor:

.. image:: media/unidad-medida-5.png
   :align: center
   :scale: 75 %

Ahora prestemos atención a la categoría "Unidad".

Odoo trae precargadas dos uom para esa categoría:

.. image:: media/unidad-medida-6.png
   :align: center
   :scale: 75 %

En nuestro ejemplo vamos a agregar otra uom para las centenas. La relación con la unidad de medida de 
referencia para la categoría "Unidad" será más grande con un ratio de 100.

.. image:: media/unidad-medida-7.png
   :align: center
   :scale: 75 %

.. image:: media/unidad-medida-7-1.png
   :align: center
   :scale: 75 %

*************************************************
Pedido de compra
*************************************************

Ahora vamos a crear el producto nuevo y le vamos a indicar la uom y uom de compra.
Esto lo hacemos desde la pestaña "Información general":

.. image:: media/unidad-medida-8.png
   :align: center
   :scale: 75 %

Ahora vamos a cargar un pedido de compra al proveedor por el producto. 

En la imagen podemos apreciar que Odoo automáticamente toma la uom de compra:

.. image:: media/unidad-medida-9.png
   :align: center
   :scale: 75 %

Confirmemos el pedido de compra y observemos el movimiento de recepción que nos genera en el inventario.

Odoo convierte automáticamente la uom de compra a la uom de venta, y de esta manera se manejará a partir de ahí
en el stock de Odoo.

.. image:: media/unidad-medida-10.png
   :align: center
   :scale: 75 %

