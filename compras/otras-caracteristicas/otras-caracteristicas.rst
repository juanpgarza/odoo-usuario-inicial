###################################################################################################
Otras caracteristicas
###################################################################################################

Si consultamos la opción de menú Configuración/Ajustes de la App de Compras, 
podremos observar que Odoo nos permite activar (desactivar) algunas caracteristicas extras.

Vamos a ver algunos ejemplos:

*************************************************
Aprobación de pedidos
*************************************************

Esta funcionalidad permite que una persona con la responsalibilidad suficiente pueda autorizar las Compras
que superan un importe determinado.

Veamos un ejemplo en la base de datos computotal-dev:

En Compras/Configuración/Ajustes/Pedidos, indicar que los pedidos que superen los $ 5.000 requieran una aprobación:

.. image:: media/oc-pedidos-aprobacion-1.png
   :align: center
   :scale: 75 %

Elijamos un usuario que tiene los permisos mínimos para la aplicación de compras. El permiso mínimo es "Usuario" y el 
máximo "Responsable":

.. image:: media/oc-pedidos-aprobacion-2.png
   :align: center
   :scale: 75 %

Y un usuario con los permisos máximos. En este caso elijo el usuario admin:

.. image:: media/oc-pedidos-aprobacion-2.png
   :align: center
   :scale: 75 %

Iniciemos sesión con el usuario con permisos mínimos:

.. image:: media/oc-pedidos-aprobacion-3.png
   :align: center
   :scale: 75 %

Cargamos una SdP con un importe que supere los $ 5.000:

.. image:: media/oc-pedidos-aprobacion-4.png
   :align: center
   :scale: 75 %

Cuando confirmamos el pedido, vemos que lo deja en un nuevo estado "Para Aprobar".

Como este usuario no tiene los permisos sufientes, depende de otro que sí los tiene
para continuar con el flujo.

.. image:: media/oc-pedidos-aprobacion-5.png
   :align: center
   :scale: 75 %

Ahora iniciemos sesión con el usuario admin. Y consultemos la vista lista. Observamos
que existe un pedido en estado "Para Aprobar".

.. image:: media/oc-pedidos-aprobacion-6.png
   :align: center
   :scale: 75 %

Consultamos la vista individual y vemos que Odoo nos propone con paso siguiente "Aprobar Pedido".
Continuando con el ejemplo, aprobemos el pedido:

.. image:: media/oc-pedidos-aprobacion-7.png
   :align: center
   :scale: 75 %

Con esto se completa el circuito de aprobación y el pedido queda confirmado.

Si consultamos el Openchatter en este mismo formulario, podemos observar el detalle de todos los 
pasos que se fueron dando:

.. image:: media/oc-pedidos-aprobacion-8.png
   :align: center
   :scale: 75 %

*************************************************
Avisos
*************************************************

La funcionalidad de "Avisos" está presente en varias aplicaciones de Odoo.

En el caso de la aplicación de Compras, permite que el usuario reciba advertencias 
en pedidos relacionadas con proveedores y/o productos.

Veamos un ejemplo.

En Compras/Configuración/Ajustes/Pedidos/Avisos, tildemos la opción "Avisos":

.. image:: media/oc-pedidos-avisos.png
   :align: center
   :scale: 75 %

Ahora editemos la vista individual de nuestro proveedor. 

Observaremos que en la pestaña
"Notas Internas", en la sección "Aviso en el pedido de compra" podemos elegir desde una lista 
de opciones:

- Sin mensaje: comportamiento habitual. No muestra ningún mensaje.
- Aviso: muestra un mensaje y deja seguir con el flujo.
- Mensaje de bloqueo: muestra un mensaje y no permite continuar con el pedido.

.. image:: media/oc-pedidos-avisos-1.png
   :align: center
   :scale: 75 %

En nuestro ejemplo, seleccionamos Aviso. y escribimos un texto descriptivo:

.. image:: media/oc-pedidos-avisos-2.png
   :align: center
   :scale: 75 %

Ahora si vamos a Compras/Solicitudes de presupuesto, y seleccionamos al proveedor al proveedor,
nos va a mostrar el aviso correspondiente:

.. image:: media/oc-pedidos-avisos-3.png
   :align: center
   :scale: 75 %

Ahora analicemos el tema de los avisos pero para el caso de los productos.

Para esto vamos a editar la vista individual de uno de los productos que tenemos cargados.
Yo elijo "Dvd Virgen".

En la pestaña "Notas", en la sección "Aviso cuando compra este producto", vemos algo similiar al
caso de los proveedores.

Ahora vamos a seleccionar el tipo "Mensaje de bloqueo" y vamos a ingresar un texto descriptivo:

.. image:: media/oc-pedidos-avisos-4.png
   :align: center
   :scale: 75 %

De la misma forma que en el caso anterior, vamos a cargar un pedido. Elegimos el proveedor y luego
en el detalle de productos, indicamos "Dvd Virgen".

Vamos a ver que nos muestra el mensaje y luego la lista de selección queda vacía. Esto nos impide 
hacer un pedido de este producto:

.. image:: media/oc-pedidos-avisos-5.png
   :align: center
   :scale: 75 %
