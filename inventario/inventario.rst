##################
Inventario
##################

Configurar inventario inicial
=============================

Ejemplo de como configurar el stock inicial de los productos. Esta tarea
es parte de la configuración inicial de la App inventario.

Base de datos utilizada: Computotal-dev

Instalar la App Gestión de inventario.

La opción de configuración “Almacenes” muestra que actuamente tenemos un
solo depósito configurado. Observar que no da la opción de agregar otro
depósito.

|image0|

La opción de configuración “Tipos de operaciones” muestra los tipos de
operaciones que están actualmente configuradas.

Observar que las únicas operaciones admitidas son:

    *Recepciones*: para recibir los productos que compramos a nuestros
    proveedores;

*Órdenes de entrega*: para realizar la entrega de pedidos a nuestros
clientes.

|image1|

Si consultamos el producto Mouse vemos que solo nos muestra la
descripción y el precio:

|image2|

Editamos el producto y seleccionamos “Producto Almacenable” en el campo
tipo de producto. Esto nos va a permitir controlar los movimientos de
stock en los almacenes.

|image3|

Ahora si volvemos a consultar el producto vemos que además de la
descripción y el precio, nos informa la cantidad actual de stock. Es 0
unidades en este momento.

|image4|

Volvemos a consultar el producto “Mouse” y seleccionamos la opción
“Actualizar cantidad disponible”. Esto nos va a permitir informar el
stock actual.

|image5|

Informamos 10 como la nueva cantidad en mano:

|image6|

Ahora consultamos la vista tarjeta de productos y vemos que la nueva
cantidad en stock es 10 unidades:

|image7|

Cargar y Confirmar pedido de ventas
===================================

Vamos a ver como la confirmación y entrega de un pedido afecta la
cantidad en stock.

Base de datos utilizada: Computotal-dev

1. Cargamos un pedido de 2 unidades del producto mouse:

|image8|

2. Confirmamos el pedido y seleccionamos la opción “Entrega” (Botón inteligente del camioncito)

|image9|

Esto nos lleva al formulario de salida de stock que nos va a permitir
confirmar la entrega.

3. Hacemos clic en validar para confirmar.

|image10|

Como no indicamos la cantidad del producto que el cliente retira (puede
retirar menos si lo desea), el sistema nos avisa que va a suponer que el
cliente retira el total del pedido:

|image11|


4. La orden de entrega cambia al estado "Hecho".
Desde la opción "Imprimir" podremos imprimir el remito de salida de la 
mercadería.

.. image:: media/orden-entrega-100.png
   :align: center
   :scale: 75 %

5. Ahora consultamos el stock y vemos disminuyo en 2 unidades (10-2=8)

|image12|

Informes de inventario
======================

Base de datos utilizada: Computotal-dev

|image13|

Inventario
----------

|image14|

|image15|

Valoración del inventario
-------------------------

|image16|

|image17|

Movimientos de producto
-----------------------

|image18|

Empresa con múltiples depósitos
===============================

[INTRO]

Demostración de las funcionalidades que incorpora Odoo para la migración
de información.

Base de datos utilizada: Computotal-dev

Activar opción Multialmacen
---------------------------

|image19|

Se agrega la opción de menú Ubicaciones.

|image20|

Se habilita la opción de crear (e importar) almacén:

|image21|

Se agrega un tipo de operación nueva: Transferencias internas.

|image22|

Crear un almacén y ubicaciones
------------------------------

Crear un nuevo almacén y llamarlo “Depósito”

|image23|

Renombrar el almacen “Computotal”. Llamarlo “Comercio”.

|image24|

Renombrar la ubicación interna “Stock” del almacen Depósito. Llamarla
“Estantería A”.

|image25|

Agregar la ubicación “Estantería B” en el almacén Depósito.

|image26|

El esquema de ubicaciones queda así:

|image27|

Almacén de entrega en pedido
----------------------------

Cargar un pedido nuevo. Observar que en el campo “Almacén” nos permite
indicar el lugar desde donde se va a entregar el pedido al cliente.

|image28|

Transferencia internas
----------------------

Hagamos un ejemplo del nuevo tipo de operación: “transferencia interna”.

En el tablero de la App Inventario, seleccionamos “Transferencia
inmediata” en el menú desplegable de Transferencias internas del almacén
“Comercio”:

|image29|

Dejar la ubicación origen por defecto (COME/Stock) y en ubicación
destino elegir “DEPO/Estantería A”

|image30|

Informar en la pestaña Operaciones el producto mouse y en la columna
Hecho 3 unidades. Validar la operación.

Con esto queda confirmado el movimiento de stock desde el almacen
Comercio al Depósito.

|image31|

Ahora consultemos el stock actual desde la opción Informes/Inventario

Vemos que la cantidad de producto “Mouse” aumento en 3 en la ubicación
“DEPO/Estantería A” y disminuyo en la misma cantidad en COME/Stock.

|image32|

Reglas de abastecimiento
========================

Vamos a ver con un ejemplo como funcionan las reglas de abastecimiento.
Estás nos permiten automatizar parte de nuestro proceso de reposición de
los productos vendidos.

Base de datos utilizada: Computotal-dev

Antes que nada deberemos instalar la App Gestión de compras.

Vamos a tomar como ejemplo el producto “Mouse”. En la opción de consulta
vemos que en este momento no tiene reglas de abastecimiento informadas
(ver botón inteligente)

|image33|

Vamos a hacer clic en el botón inteligente para agregar una regla.
Informamos los campos tal cual se muestran en la siguiente imagen:

|image34|

Cuando guardamos, volvemos a la consulta del producto y vemos que ahora
nos muestra los datos de Mínimo y Máximo en el botón inteligente:

|image35|

El paso siguiente es dar de alta un proveedor ficticio:

|image36|

Luego, editaremos nuevamente el producto Mouse y seleccionaremos “Añadir
un elemento” en la lista que se encuentra en la pestaña “Compra”:

|image37|

En el siguiente formulario deberemos informar los campos tal cual
muestra la imagen:

|image38|

Luego seleccionar “Guardar y Cerrar”.

También deberemos tildar (puede que ya este tildada) la opción Comprar
dentro de la sección Operaciones de la pestaña “Inventario”:

|image39|

En este paso de verificación, vemos que hasta el momento no tenemos
ninguna Solicitud de presupuesto (SdP) cargada:

|image40|

Este es otro paso de verificación. Aquí verificamos que la cantidad en
stock del producto Mouse en la ubicación COME/Stock es de 2 unidades:

|image41|

El próximo paso es Ejecutar el planificador (en Inventario/Operaciones).
Cuando lo seleccionamos nos muestra el aviso:

|image42|

Nos esta diciendo que en caso de que corresponda activará reglas de
abastecimiento.

Como en nuestra regla de ejemplo le indicamos que el mínimo del producto
en la ubicación COME/Stock era de 10 unidades y actualmente tenemos solo
2 unidades, se debería haber generado un SdP para el producto.

Consultamos la SdP generada para analizar los valores con los que fue
creada.

Emitida al proveedor “Más Tecnología” porque es el que el que le
asociamos en el formulario de producto. En ese mismo lugar le indicamos
que el importe era de $ 100 y que el tiempo de inicial de entrega era de
2 días. Este último dato lo utiliza para calcular la fecha prevista
(fecha actual + 2 días).

Por una cantidad de 28 unidades. Porque lo tiene que llevar hasta 30 que
es el máximo que le informamos en la regla y solo tenía 2 unidades.

|image43|

Confirmamos la SdP, lo que significa que hemos decidido confirmar el
presupuesto al proveedor. Quedamos a la espera del envío del producto.

Recepciones
===========

El último tipo de operación que nos queda por analizar son las
Recepciones. Representa el movimiento de stock que le da ingreso a los
pedidos que envian los proveedores.

Base de datos utilizada: Computotal-dev

Cuando confirmamos una SdP, el sistema genera en forma automática el
movimiento de recepción correspondiente en el estado Preparado.

Si consultamos la SdP podemos “navegar” hacia la recepción por medio del
botón inteligente “Envio”

|image44|

En el envío podemos ver que los datos se corresponden con la SdP. Es
más, podemos ver que el campo “Documento origen” representa la
vinculación entre los 2 documentos:

|image45|

Si validamos el movimiento, nos mostrará la siguiente advertencia:

|image46|

El sistema nos está indicando que va a suponer que el envío incluye el
total de unidades solicitado (no es una entrega parcial). Esto sucede
porque no le indicamos la cantidad que recibimos. Este dato se tendría
que completar en la columna hecho. De todas maneras solo se necesita en
el caso de las entregas parciales.

Si consultamos los movimientos de producto, podemos ver el nuevo
movimiento al final de la lista:

|image47|

Y si consultamos la cantidad en stock, vemos que aumento a 30 unidades
en la ubicación Come/Stock:

|image48|

.. |image0| image:: ./media/image1.png
   :width: 5.90556in
   :height: 1.75347in
.. |image1| image:: ./media/image2.png
   :width: 5.90556in
   :height: 1.73472in
.. |image2| image:: ./media/image3.png
   :width: 4.51667in
   :height: 1.92213in
.. |image3| image:: ./media/image4.png
   :width: 3.85000in
   :height: 2.30031in
.. |image4| image:: ./media/image5.png
   :width: 4.27222in
   :height: 2.10446in
.. |image5| image:: ./media/image6.png
   :width: 5.03889in
   :height: 1.99268in
.. |image6| image:: ./media/image7.png
   :width: 4.20556in
   :height: 1.74622in
.. |image7| image:: ./media/image8.png
   :width: 4.19444in
   :height: 2.24716in
.. |image8| image:: ./media/image9.png
   :width: 5.90556in
   :height: 3.05833in
.. |image9| image:: ./media/image10.png
   :width: 5.90556in
   :height: 2.21944in
.. |image10| image:: ./media/image11.png
   :width: 5.90556in
   :height: 2.81597in
.. |image11| image:: ./media/image12.png
   :width: 4.30307in
   :height: 1.33889in
.. |image12| image:: ./media/image13.png
   :width: 4.09444in
   :height: 2.83539in
.. |image13| image:: ./media/image14.png
   :width: 1.91667in
   :height: 1.82736in
.. |image14| image:: ./media/image15.png
   :width: 3.27222in
   :height: 2.48192in
.. |image15| image:: ./media/image16.png
   :width: 4.97778in
   :height: 1.48327in
.. |image16| image:: ./media/image17.png
   :width: 4.83333in
   :height: 2.37688in
.. |image17| image:: ./media/image18.png
   :width: 5.90556in
   :height: 1.90556in
.. |image18| image:: ./media/image19.png
   :width: 5.90556in
   :height: 1.92708in
.. |image19| image:: ./media/image20.png
   :width: 5.90556in
   :height: 2.49583in
.. |image20| image:: ./media/image21.png
   :width: 2.23333in
   :height: 1.92696in
.. |image21| image:: ./media/image22.png
   :width: 5.90556in
   :height: 2.84236in
.. |image22| image:: ./media/image23.png
   :width: 5.90556in
   :height: 2.53681in
.. |image23| image:: ./media/image24.png
   :width: 4.10556in
   :height: 2.15078in
.. |image24| image:: ./media/image25.png
   :width: 4.13333in
   :height: 2.22512in
.. |image25| image:: ./media/image26.png
   :width: 5.90556in
   :height: 1.99306in
.. |image26| image:: ./media/image27.png
   :width: 5.48889in
   :height: 4.17540in
.. |image27| image:: ./media/image28.png
   :width: 5.90556in
   :height: 2.26042in
.. |image28| image:: ./media/image29.png
   :width: 4.52222in
   :height: 3.96652in
.. |image29| image:: ./media/image30.png
   :width: 5.53333in
   :height: 2.67948in
.. |image30| image:: ./media/image31.png
   :width: 4.77222in
   :height: 3.43326in
.. |image31| image:: ./media/image32.png
   :width: 5.48333in
   :height: 2.62173in
.. |image32| image:: ./media/image33.png
   :width: 5.90556in
   :height: 2.68681in
.. |image33| image:: ./media/image34.png
   :width: 5.55556in
   :height: 2.88622in
.. |image34| image:: ./media/image35.png
   :width: 5.55000in
   :height: 2.92315in
.. |image35| image:: ./media/image36.png
   :width: 5.78333in
   :height: 2.31497in
.. |image36| image:: ./media/image37.png
   :width: 4.84444in
   :height: 2.85688in
.. |image37| image:: ./media/image38.png
   :width: 4.20556in
   :height: 2.95536in
.. |image38| image:: ./media/image39.png
   :width: 5.62222in
   :height: 2.71921in
.. |image39| image:: ./media/image40.png
   :width: 4.48333in
   :height: 3.19801in
.. |image40| image:: ./media/image41.png
   :width: 5.64444in
   :height: 2.08414in
.. |image41| image:: ./media/image42.png
   :width: 4.78333in
   :height: 1.68350in
.. |image42| image:: ./media/image43.png
   :width: 5.09444in
   :height: 1.51563in
.. |image43| image:: ./media/image44.png
   :width: 5.33333in
   :height: 3.83819in
.. |image44| image:: ./media/image45.png
   :width: 5.90556in
   :height: 2.76250in
.. |image45| image:: ./media/image46.png
   :width: 5.90556in
   :height: 2.90833in
.. |image46| image:: ./media/image47.png
   :width: 4.82222in
   :height: 1.63595in
.. |image47| image:: ./media/image48.png
   :width: 5.13333in
   :height: 2.45198in
.. |image48| image:: ./media/image49.png
   :width: 5.90556in
   :height: 2.28819in
