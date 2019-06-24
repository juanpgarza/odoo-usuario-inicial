Primeros pasos con Odoo
=======================

Introducción
------------

Los temas que veremos incluyen:

-  Configurar una base de datos protegida por una contraseña

-  Instalar y configurar la aplicación de gestión de ventas

-  Usar las caracteristicas de la interface de usuario para ver, editar
       y encontrar información

-  Dar de alta un cliente nuevo

-  Agregar nuestro primer producto para vender

-  Configurar la información de la empresa

-  Completar un pedido de ventas y confirmarla para luego facturarla.

Crear una base de datos nueva
-----------------------------

El primer paso después de instalar Odoo es crear una base de datos para
nuestra empresa.

Si acabamos de instalar una copia limpia de Odoo, Odoo nos muestra
automáticamente la pantalla para crear la db.

En la siguiente captura de pantalla podemos ver el formulario para crear
base de datos de Odoo:

|image0|

Odoo provee instrucciones básicas de como crear una base de datos.

Vamos a ver los campos uno a uno.

Nombre de la base de datos
~~~~~~~~~~~~~~~~~~~~~~~~~~

Al elegir el nombre de la db, debemos elegir uno que describa el sistema
y que deje en claro el propósito de la base de datos.

Algunas pocas reglas:

1. El nombre no puede contener espacios en blanco y debe comenzar con un
   número o una letra

2. Debemos evitar las comas, puntos y comillas

3. Los guiones bajos y guiones medios son permitidos si no son el primer
   carácter del nombre

Es una buena idea, especificar en el nombre si el propósito de la base
de datos es desarrollo, testing o producción.

Para entender mejor como trabajar con Odoo, vamos a construir nuestros
ejemplos con un caso de estudio del mundo real.

Para el propósito de nuestro ejemplo del mundo real, vamos usar el
nombre “computotal-dev”.

Elegimos -dev porque consideramos que será una base de datos de
desarrollo, que no usaremos para producción ni para testing.

Podriamos definir como un estándar:

-dev para desarrollo

-test para testing

-prod para producción

Email y Password
~~~~~~~~~~~~~~~~

El mail que le informamos Odoo lo toma como el usuario administrador (o
superusuario)

Y el password será el de esta cuenta de usuario administrador.

Por ahora vamos a informar admin, admin.

Idioma por defecto
~~~~~~~~~~~~~~~~~~

Vamos a usar Spanish (AR) / Español (AR) y en país “Argentina”.

Datos de demostración
~~~~~~~~~~~~~~~~~~~~~

Si marcamos este check cuando creamos la db, odoo pre-cargará las tablas
con un conjunto de datos de ejemplo para cada modulo que instalemos.
Esto podría incluir clientes, proveedores, pedidos de venta, facturas,
movimientos de stock, etc FALSOS.

El objetivo de los datos de demostración es poder recorrer los módulos
del sistema sin la necesidad de tipear una cantidad enorme de datos de
prueba.

Nunca cargaremos los datos de demo si vamos a usar la db en producción.

Para nuestro caso de estudio del mundo real, no cargaremos los datos de
ejemplo.

Seleccionar “Create database” para que comience el proceso de generación
de la base de datos de Odoo. El proceso puede demorar unos minutos.

Administrar base de datos en Odoo
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

La interface de administración de db de Odoo permite realizar tareas
básicas de administración tales como realizar backup o restaurar una
base de datos.

Con Odoo es posible administrar nuestras base de datos sin tener que
acceder al servidor Postgres (Tecnología de base de datos de Odoo).

También es posible configurar muchas base de datos en la misma
instalación de Odoo. Por ejemplo, en el futuro podríamos querer instalar
otra base de datos con datos de prueba y usarla para instalar módulos
con fines de prueba.

Podemos acceder al administrador en forma directa desde la url
http://localhost:8069/web/database/manager.

|image1|

En esta simple interface, podremos crear, hacer backup, duplicar,
eliminar y restaurar bases de datos.

Seguridad para el administrador de base de datos
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Además, podremos setear un “master password” para el administrador de
base de datos de Odoo.

Se debe hacer click en “Set Master Password”. A diferencia del password
que seteamos para la db “computotal-dev”, este password es para prevenir
el acceso al administrador de base de datos.

Este es un paso importante en la seguridad de la instalación de Odoo y
la advertencia debería tomarse enserio. Si no seteamos esta contraseña,
entonces cualquiera podría realizar todas estas operaciones.

Aplicaciones
------------

Odoo “de fabrica” incluye muchas aplicaciones que pueden se pueden
instalar y utilizar. Ej. CRM, Proyectos, Gestión de inventarios,
Fabricación, Gestión de ventas, etc.

En esta captura de pantalla se muestra la opción de menú Aplicaciones,
desde donde se pueden consultar e instalar las aplicaciones disponibles:

|image2|

En cada nueva versión de Odoo se siguen agregando nuevas aplicaciones.
En Odoo 11 (la versión sobre la que vamos a trabajar) se agrega por
ejemplo, la aplicación “Constructor de sitios web”, que permite crear
sitios web de la misma forma que lo podemos hacer con wordpress.

Independientemente de la cantidad de apps que incluye Odoo, el proceso
de implementación (puesta en marcha) es el mismo.

Comienza analizando las necesidades del negocio como un todo y luego se
decide cual va a ser el primer conjunto de aplicaciones que deseamos
implementar.

Definir las necesidades
-----------------------

Implementar un software como Odoo no es una tarea sencilla. Muchas
empresas se meten en problemas porque creen que es solo instalar el
software, ingresar algunos datos y listo.

Inevitablemente el alcance del proyecto va a crecer y lo que se suponía
que iba a ser un sistema simple termina siendo algo muy confuso.

Afortunadamente Odoo tiene un diseño modular que permite adoptar una
estrategia sistematica para implementar Odoo en un negocio.

Implementar usando una estrategia modular
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

La instalación mínima de Odoo (apenas creamos una base de datos) no
incluye ninguna aplicación.

Dentro de la implementación de Odoo el primer paso será definir con que
módulos queremos trabajar primero.

Odoo nos permite instalar solo lo que necesitamos ahora y después seguir
instalando módulos medida que vamos teniendo más claras las necesidades
de la empresa.

Podriamos comenzar instalando la gestión del inventario y luego
continuar con la venta y la facturación. O bien comenzar con las ventas
y facturación y luego agregar la gestión del inventario.

TIP/Recomendación: no instalar y poner a funcionar todos los módulos de
una sola vez. Lo ideal es dividir la implementación en fases más
pequeñas.

Computotal: un caso del mundo real
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Para entender mejor como trabajar con Odoo, vamos a construir nuestros
ejemplos con un caso de estudio del mundo real.

Computotal es una empresa pequeña cuya actividad principal es la compra
y venta de artículos de computación.

Usando el diseño modular de Odoo, vamos a comenzar implementando la
aplicación “Gestión de ventas” para venta básica de productos (partes de
computadoras en este caso).

Luego, a medida que vamos avanzando con el curso, iremos instalando
módulos adicionales.

Instalar el módulo de Gestión de ventas
---------------------------------------

Luego de clickear “Create Database”, pasará un tiempo (mayor o menor
dependiendo de tu sistema) hasta que se muestre una página con una lista
de las aplicaciones disponibles.

|image3|

Esta es la lista de las aplicaciones más comunes que podermos instalar.

Es muy poco lo que podemos hacer con una base de datos Odoo sin módulos
instalados. Ahora, instalaremos la aplicación “Gestión de ventas” así
podemos comenzar a configurar nuestro negocio que vende componentes
informáticos.

|image4|

Clikeamos en el botón instalar para instalar el módulo de “Gestión de
ventas”.

Mientras los módulos se instalan y durante otras operaciones largas,
siempre veremos un icono “Cargando” arriba y en el centro de la
pantalla. En estos casos, Odoo completará la operación sin la necesidad
de la intervención del usuario.

Básicos de la UI de Odoo
------------------------

Luego de la instalación de la aplicación, Odoo 11 nos lleva al menú
“Debates”, que es nuestra bandeja de entrada y donde las actividades de
comunicación tienen lugar.

Podemos observar que Odoo muestra una lágrima pequeña de color purpura
que provee tips muy útiles. Estos se mostrarán en la mayoría de las
aplicaciones que instalemos.

|image5|

Como podemos observar, los menus de las aplicaciones están en la parte
superior de la interface.

Si clikeamos el menú “Ventas”, nos llevará a la aplicación “Ventas”.
Esto te lleva directamente al dashboard (Tablero) de ventas. Como recien
acabamos de instalar la aplicación, habrá muy poco para ver. Pero
podremos ver las opciones de menú disponibles en la parte izquieda de la
interface.

Los menús en la parte superior nos permiten cambiar entre las
aplicaciones principales instaladas y la configuración de Odoo. Mientras
que el menu en la parte izquierda, nos mostrará las opciones disponibles
en la aplicación actual.

En la siguiente captura de pantalla, estamos posicionados en el menu
principal “Ventas”:

|image6|

La primer opción de menú que aparece por defecto es **Presupuestos**.
Como todavía no cargamos ningun presupuesto, Odoo nos muestra
instrucciones útiles sobre como crear un presupuesto.

Por ahora, observemos uno de los conjuntos de registros más importantes
que vamos a estar utilizando en muchas de las aplicaciones de Odoo:
**Clientes**. Hagamos Click en el menú **Clientes** en la parte
izquierda.

Tomaremos un momento para analizar algunos elementos de la interface de
usuario que aparecerán de forma consistente en todo Odoo. Arriba a la
izquierda del formulario principal, podemos ver claramente que estamos
en la sección **Clientes**.

Usar el cuadro de búsqueda
~~~~~~~~~~~~~~~~~~~~~~~~~~

En la esquina superior derecha de nuestro formulario, tenemos un cuadro
de búsqueda:

|image7|

El cuadro de búsqueda nos permite buscar rápidamente registros en una
aplicación Odoo. Si estamos en la sección **Clientes**, naturalmente la
búsqueda se realizará sobre los registros de clientes.

De la misma manera, si estamos buscando en la vista **Producto**, el
cuadro de búsqueda nos permitirá buscar registros de productos que hemos
cargado en el sistema.

Elegir vistas diferentes
~~~~~~~~~~~~~~~~~~~~~~~~

Odoo también ofrece una interface estandar para cambiar entre una *vista
Kanban* (Tarjetas) y una *vista lista*. En algunos formularios tendremos
opciones adicionales como la *vista gráfico*.

Podemos ver iconos de selección debajo del cuadro de búsqueda en la
esquina derecha del formulario:

|image8|

La vista seleccionada actualmente está resaltada con gris oscuro. Si
movemos el mouse sobre el icono, obtendremos un tooltip que nos muestra
la descripción de la vista.

Vamos a cargar registros para poder explorar mejor la inteface de Odoo.

Crear el primer cliente
-----------------------

Odoo nos muestra instrucciones útiles para comenzar a cargar nuestro
primer cliente. Hacemos Click en el botón Crear:

|image9|

Este es el formulario de **Clientes**. Haciendo click en Crear
generaremos un registro de cliente.

Computotal vende componentes de forma mayorista y minorista. En este
ejemplo, vamos a usar un cliente ficticio llamado *Armando Lio* que
desea comprar Mouse.

Odoo ofrece flexibilidad en la carga de información del cliente ya que
por defecto, la mayoría de los campos son no requeridos. Los campos en
púrpura, siempre serán requeridos.

En odoo 11, el único campo requerido para el cliente es el nombre. El
resto son opcionales. Más adelante, veremos como hacer que los campos
opcionales pasen a ser obligatorios.

En este ejemplo, hemos completado alguno de los campos básicos de
nuestro cliente ficticio, *Armando Lio*:

|image10|

El cliente es una empresa?
~~~~~~~~~~~~~~~~~~~~~~~~~~

Al principio del formulario está una selección para indicarle a Odoo si
el cliente es un individuo o una compañía. En nuestro ejemplo, estamos
simulando una compra minorista de un cliente que es una persona.

Si estamos haciendo una operación del tipo B2B (Negocio a Negocio),
entonces lo habitual será que el cliente sea una empresa.

Ingresar datos en un formulario
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Interface consistente
^^^^^^^^^^^^^^^^^^^^^

Odoo utiliza una interface para el ingreso de datos que se mantiene
consistente en todo la aplicación. Una vez que aprendimos como ingresar
datos en un formulario, no deberíamos tener problemas ingresando datos
en los demás formularios de Odoo.

Campos obligatorios – Navegar entre campos
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Los campos obligatorios siempre estarán en púrpura. Si vemos campos en
púrpura, deberemos ingresar datos en ellos para que Odoo nos permitar
guardar el registro.

Para movernos entre los campos de un formulario podemos usar el mouse o
la tecla *Tab*. Con la combinación *Shift + Tab* podremos volver al
campo anterior. A diferencia de algunos sistemas, no podremos movernos
entre campos usando las teclas de flechas o el enter.

Listas de selección
'''''''''''''''''''

En muchos formularios encontraremos listas de selección que nos
permitiran elegir de una lista de elementos para llenar el campo.

Reducir resultados
''''''''''''''''''

Podemos usar el teclado para ingresar alguna parte del texto buscado y
así reducir los elementos que se muestran en la lista de selección.

Si seleccionamos primero el país (Ej. Argentina), la lista de provincias
solo mostrará las provincias correspondientes a ese país.

Odoo trae pre-cargado de fábrica muchos países con sus correspondientes
provincias. Argentina y sus provincias vienen pre-cargadas.

Debemos tener cuidado cuando estemos buscando palabras con asento porque
Odoo los tiene en cuenta para las búsquedas. Ej. para buscar la
provincia “Río Negro”, ingresamos “Rio” debemos agregar el acento a la i
ya que la esa palabra esta cargada con asento en Odoo.

Minimizar uso del Mouse
'''''''''''''''''''''''

Podemos movernos entre los elementos de la lista usando las teclas de
flechas y tabular para seleccionar el elemento que queremos cargar. Esto
nos permite ingresar datos en los formularios de Odoo minimizando el uso
del mouse.

Buscar más – Crear y Editar
'''''''''''''''''''''''''''

Muchas listas de selección tienen dos opciones al final que nos
permitiran usar opciones de búsqueda adicionales o crear un elemento
nuevo que no está en la lista.

|image11|

En este ejemplo podemos ver la lista de provincias con la opcion de
buscar más o de crear una provincia nueva para el caso de que no se
encuentre cargada.

Idioma
^^^^^^

Odoo da la posibilidad de trabajar con clientes que hablan una variedad
de idiomas. En nuestro ejemplo vamos a dejar el que Odoo nos propone por
defecto: Español. Pero en el caso de que estemos trabajando con un
cliente que prefiera sus documentos en otro idioma, podemos espeficar
ese idioma y Odoo se encargará de gestionar la traducción necesaria.

Notas Internas
^^^^^^^^^^^^^^

Esta sección permite ingresar cualquier información adicional que se
desee mantener del cliente.

Pestaña “Ventas y Compras”
~~~~~~~~~~~~~~~~~~~~~~~~~~

La parte inferior de la pantalla de clientes está divida en una serie de
pestañas que ayudan a organizar la información.

En la pestaña Ventas y Compras, podemos ver opciones tales como el
vendedor u otras opciones relacionadas con las ventas.

|image12|

Es Cliente / Es Proveedor
^^^^^^^^^^^^^^^^^^^^^^^^^

Odoo guarda todos los individuos en la misma tabla, independientemente
de si se trata de un cliente o un proveedor. El hecho de que el campo
“Es cliente” esté tildado, le indicará a Odoo que el registro se trata
de un cliente.

Debemos tildar este campo para que Odoo reconozca a Armando Lio como un
cliente.

El campo Es proveedor nos permite indicar que se trata de un proveedor.
Una empresa (o persona) podrá ser cliente y proveedor al mismo tiempo.

Vendedor
^^^^^^^^

Nos permite indicar cual será el vendedor asignado a este cliente.
Aunque no es obligatorio, por lo general se informa cuando estamos
integrando nuestro sistema de gestión de ventas con el módulo de CRM.
Usaremos este campo cuando estudiemos el CRM de Odoo, por ahora lo
dejaremos en blanco.

Referencia interna
^^^^^^^^^^^^^^^^^^

Por lo general, cuando implementamos Odoo, la empresa ya posee un
sistema de numeración para los clientes. El campo Referencia interna, es
perfecto para completar con el número de cliente que ya tiene asignado.
De otra manera, podemos dejar el campo en blanco o usarlo para otro
propósito. En nuestro ejemplo, lo dejaremos en blanco.

Pestaña “Facturación”
~~~~~~~~~~~~~~~~~~~~~

La pestaña de Facturación (antes llamada Contabilidad) nos permite
indicar información de condiciones de venta, compra e información
fiscal.

|image13|

Plazo de pago de cliente
^^^^^^^^^^^^^^^^^^^^^^^^

Es muy comun que en muchos negocios clientes diferentes tengan
diferentes plazos de pago. Quizás, para clientes con mucha antigüedad
podríamos extender el plazo a 30 o 60 días para pagar sus facturas. Y
para clientes nuevos, podríamos exigir el pago de contado.

Odoo permite configurar plazos de pagos adicionales dependiendo de
nuestras necesidades. Los plazos de pago que incluye por defecto son:

-  Pago inmediato

-  15 días

-  30 días

Para nuestro ejemplo, dejaremos con plazo 15 días.

Plazo de pago de proveedor
^^^^^^^^^^^^^^^^^^^^^^^^^^

Similar al plazo del cliente, este campo indicará el plazo de pago con
el proveedor. Como una empresa puede ser cliente y proveedor al mismo
tiempo, tenemos las condiciones separadas para cada uno.

Posicion fiscal
^^^^^^^^^^^^^^^

Hace referencia a la situación ante los impuestos. Este tema lo veremos
más en detalle cuando estudiemos la localización argentina de Odoo
(adaptación de Odoo a la legislación Argentina).

Botones Inteligentes (Smart Buttons)
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Los botones en la parte superior derecha de los formularios de Odoo se
llaman **Botones inteligentes**.

|image14|

Son de mucha utilidad ya que muestran información relacionada en forma
resumida/totalizada y permiten navegar hacia otros formularios si
queremos obtener información más detallada.

Carga de productos
------------------

Ahora que ya tenemos un cliente, es el momento de ingresar un producto
para poder venderle. En nuestro ejemplo, vamos a cargar un mouse
inalámbrico.

Hagamos clic en el menu **Productos** de la izquierda:

|image15|

Crear productos
~~~~~~~~~~~~~~~

Iniciamos la creación de un producto haciendo click en el botón Crear.

La siguiente captura de pantalla es de la pestaña de **Información
general** del formulario de productos, que usaremos para ingresar un
registro de producto en Odoo:

|image16|

Nombre del producto
^^^^^^^^^^^^^^^^^^^

Es lo que se mostrará en las pedidos de venta, facturas y en todas las
demás pantallas que se refieran a un producto específico. En nuestro
ejemplo, estamos vendiendo un “\ *mouse inalambrico genius”*.

Puede ser vendido
^^^^^^^^^^^^^^^^^

Similar a la marca de activo de un cliente, podemos marcar productos
para que no se muestren en la lista de productos de venta desmarcando
este tilde. En nuestro ejemplo, queremos poder vender este producto a
“Armando Lio” entonces la dejaremos marcada.

Puede ser comprado
^^^^^^^^^^^^^^^^^^

Aunque todavía no instalamos la aplicación de compras, Odoo nos permite
especificar si un producto puede ser comprado. Aceptaremos la opción por
defecto, entonces además de poder vender este producto también lo
podremos comprar.

Esto jugará una función importante cuando lleguemos al módulo en el que
estudiemos la aplicación de compras de Odoo.

Tipo de producto
^^^^^^^^^^^^^^^^

Es la primer opción dentro de la pestaña de información general de la
pantalla de productos.

Hay disponibles dos tipos de producto:

-  Consumible

-  Servicio

La explicación de estos tipos la veremos en detalle más adelante. Por
ahora, vamos a quedarnos con que la diferencia entre ellos es que los
Consumibles son productos reales que deben ser comprados (Ej. Mouse) y
los servicios no (Ej. limpieza de impresora).

Referencia interna
^^^^^^^^^^^^^^^^^^

En la mayoría de las pantallas de Odoo se usa el campo Nombre de
producto y la descripción cuando muestra información de productos.

Es muy habitual que la empresa ya tenga un sistema de codificación para
sus productos. El campo Referencia Interna es útil para informar estos
códigos alternativos en los productos.

En nuestro ejemplo vamos a dejar el campo referencia interna en blanco.

Precio de venta
^^^^^^^^^^^^^^^

En este campo informamos el precio de venta que se mostrará luego en el
pedido de ventas.

En nuestro ejemplo, le vamos a informar al “Mouse Inalambrico Genius” un
precio de venta de $ 500.-

Precio de costo
^^^^^^^^^^^^^^^

En este campo informamos el precio de costo. Puede ser usado para
calcular los margenes de ganancia.

Pestaña “Ventas”
~~~~~~~~~~~~~~~~

Cuando se instala la aplicación de Gestión de ventas, se crea una
pestaña “Ventas” en el formulario del producto. Pero por defecto, esta
pestaña esta completamente vacía. Luego, a medida que vamos instalando
más aplicaciones y haciendo cambios en las configuraciones, esta página
se irá llenando con información apropiada.

Esto es algo muy común en Odoo. Por eso, a medida que configuramos
nuestras aplicaciones, tenemos que asegurarnos de volver a otros
formularios ya que es muy probable que tengamos más opciones para
configurar.

Pestaña “Facturación”
~~~~~~~~~~~~~~~~~~~~~

Odoo completa los campos Impuestos de cliente y de proveedor con valores
por defecto. Esto es, Odoo sugiere estos valores y si el usuario no los
cambia, los campos mantendrán esta información.

Los valores de impuestos varían según el producto del que se trate. En
argentina, por ejemplo, la mayoría de los productos llevan un IVA
(Impuesto al valor agregado) de 21%. Pero los productos tecnologicos (la
mayoría, no todos) llevan un IVA de 10,5 %.

La siguiente captura de pantalla muestra la pestaña de Facturación del
formulario de productos:

|image17|

Podemos observar que Odoo nos permite informar múltiples impuestos para
el mismo producto. Más adelante veremos un ejemplo donde se utiliza esta
posibilidad.

Política de facturación
^^^^^^^^^^^^^^^^^^^^^^^

Por defecto, Odoo configura la facturación para que los items de las
lineas de la factura sean creados basados en la cantidad que se indica
en el pedido de ventas. Esto significa que se le realizará la factura al
cliente aunque todavía no se le haya entregado ninguno de los productos.

La otra opción es que se le facture al cliente sobre los productos
entregados. Entonces, si existen productos en el pedido de ventas que
todavía no fueron entregados, no se le realizará la factura al cliente
por esos productos.

Pestaña “Notas”
~~~~~~~~~~~~~~~

Esta sección permite ingresar cualquier información adicional que se
desee mantener del producto.

Guardar el registro del producto
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Si hacemos clic en el botón guardar se almacena el registro del producto
en Odoo. Si elegimos Descartar, recibiremos una advertencia de que
perderemos los cambios realizados.

Configurar la información de la empresa
---------------------------------------

Ya cargamos un cliente y un producto. Sin embargo, antes de poder cargar
un pedido de ventas, todavía tenemos trabajo que hacer configurando
nuestra empresa (Compañía).

Actualmente Odoo ni siquiera sabe el nombre de nuestra empresa y por
defecto ha usado **My Company** como nombre.

Podemos encontrar la información de la empresa eligiendo la opción
Ajustes del menú principal y luego el botón configurar del acceso que se
encuentra en el tablero de Ajustes.

|image18|

Otra forma de acceder al mismo formulario es siguiendo el siguiente
camino: Ajustes (del menú principal) / Usuarios y Compañías / Compañias.

La siguiente captura de pantalla muestra el formulario de información de
la empresa con información para nuestro caso de estudio:

|image19|

Aquí hemos informado el nombre de la empresa, la dirección completa, el
lema, sitio web y el email.

La **moneda** se informó por defecto en pesos Argentinos (ARS) ya que
cuando configuramos la base de datos indicamos como país Argentina.

También podemos asignar un **logo** haciendo clic en el icono con la
camarita de fotos (Arriba a la izquierda).

Guardar la información de la empresa
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Hacemos clic en guardar para actualizar la información de la empresa y
ya quedamos listos para cargar nuestro primer pedido.

Crear el primer pedido
----------------------

Por fin tenemos todo listo para comenzar a vender nuestros productos.

Para acceder a la pantalla de pedidos, seleccionamos “Ventas” del menú
principal y luego pedidos del submenú de la izquierda.

En la siguiente captura de pantalla se muestran los pedidos existentes y
le permite a los usuarios crear un nuevo pedido:

|image20|

Hacemos clic en el botón crear para crear un nuevo pedido. Todo nuevo
pedido inicia como un presupuesto y permanece así hasta que confirmamos
la venta. Solo después de confirmar el presupuesto, se podrá hacer
referencia a la venta como un pedido.

La siguiente captura de pantalla muestra un formulario de pedido con el
cursor en el campo **Cliente**:

|image21|

Seleccionar el cliente
~~~~~~~~~~~~~~~~~~~~~~

Cuando creamos un pedido nuevo, Odoo nos va a pedir que primero le
indiquemos el cliente desde la lista desplegable. A medida que
agreguemos más clientes, tendremos la opción de buscar y localizar
clientes para los pedidos.

Por ahora, elegiremos el cliente que cargamos anteriormente en este
mismo capítulo.

TIP: a diferencia de versiones anteriores de Odoo, ahora podemos
comenzar a cargar renglones de pedido antes de haber informado el
cliente para el pedido.

Fecha de caducidad
~~~~~~~~~~~~~~~~~~

Por defecto no se indica nada en la fecha de caducidad del pedido. Sin
embargo, si queremos indicar una fecha a partir de la cuál el pedido no
tendrá validez, lo podemos hacer aquí:

|image22|

Funcionamiento de los campos fecha en Odoo
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

En el calendario desplegable se marca con un triangulito en la esquina
inferior derecha el día actual. Salvo que la fecha actual este
seleccionada porque en ese caso el día se marca con una figura redonda.

Si seleccionamos el mes (arriba al centro del calendario), nos llevará
al desplegable de meses. Que nos permitirá navegar entre los meses de
una forma más ágil:

|image23|

Y si luego seleccionamos el año (arriba al centro), nos mostrará el
desplegable de años para elegir el año de una forma más rápida.

|image24|

También podremos posicionarnos en el campo, borrar el contenido (tecla
backspace) y tipear nosotros mismos la fecha. Siempre respetando el
formato de fecha configurado (en este caso dd/mm/aaaa).

Plazo de pago
~~~~~~~~~~~~~

Odoo automáticamente carga los plazos de pago del cliente que
seleccionamos. Pero en el pedido siempre tendremos la opción de cambiar
el plazo para un pedido específico.

Lineas del pedido
~~~~~~~~~~~~~~~~~

Ahora ya estamos listos para comenzar a especificar el producto que
queremos vender.

Seleccionamos “Añadir un elemento” en el área de lineas del pedido para
agregar una linea a la grilla.

El primer campo será el producto. Elijamos “Mouse inalamb. Genius” de la
lista desplegable. Los demás campos de la linea de pedido se completarán
automáticamente y se verán de esta forma:

|image25|

Producto
^^^^^^^^

Cada linea de pedido comienza seleccionando un producto. Podemos agregar
productos en el mismo momento que agregamos un pedido seleccionando la
opción Crear y editar… del final de la lista.

Cuando la lista tenga más productos, se podrá usar la ventana de
busqueda de productos que se invoca con la opción Buscar más.

Despues de seleccionar el producto, Odoo carga la información de precios
e impuestos.

Descripcion
^^^^^^^^^^^

Odoo toma la descripción del registro del producto para completar el
campo Descripción en la linea del pedido. Es posible cambiar esa
descripción para un pedido específico.

Para nuestro ejemplo lo dejaremos así.

Cantidad pedida
^^^^^^^^^^^^^^^

La cantidad pedida será 1 por defecto. Obviamente podremos cambiar esta
cantidad a la cantidad de unidades que hemos vendido.

Para nuestro ejemplo dejaremos la cantidad de 1.

Precio Unitario
^^^^^^^^^^^^^^^

Odoo trae el precio de venta desde el registro del producto para cargar
el precio unitario en la linea del pedido. También es posible
sobreescribir este valor.

En nuestro ejemplo dejaremos el precio unitario en $ 500.-

TIP: se debe tener cuidado cuando se cambien precios en la linea del
pedido. Es posible que si se vuelve atrás hacia el campo Producto, el
precio unitario se cambie nuevamente al valor que tiene indicado en el
registro del producto.

La recomendación es que si se está cambiando precios en las lineas de
pedidos, se debe controlar dos veces los precios unitarios, antes de
confirmar el pedido.

Impuestos
^^^^^^^^^

Odoo soporta impuestos por cada linea de pedido. Automáticamente traerá
el 10,5% de IVA indicado para el registro del producto. Impuestos
adicionales pueden ser agregados o quitados de la linea.

Para nuestro ejemplo dejaremos el impuesto de 10,5% de IVA.

Subtotal
^^^^^^^^

El subtotal se calcula automáticamente como la multiplicación del precio
unitario por la cantidad.

Procederemos a guardar un pedido como un presupuesto.

Workflow de un pedido
~~~~~~~~~~~~~~~~~~~~~

El workflow habitual de un pedido es: Presupuesto -> Presupuesto Enviado
-> Pedido de ventas

Aunque comenzamos ingresando un pedido, el estado actual del pedido es
Presupuesto. Odoo 11 muestra el estado actual de las transacciones en la
esquina superior derecha del formulario.

|image26|

Este indicador hace muy fácil visualizar el estado actual de una
transacción atravez del workflow de Odoo. En este ejemplo, podemos ver
que el estado actual es “Presupuesto”.

También podemos observar que el presupuesto normalmente debe ser enviado
antes de que el pedido pueda considerarse realizado.

Las acciones disponibles que podemos tomar sobre este presupuesto se
muestran en la esquina superior izquierda del formulario.

La siguiente captura de pantalla muestra las acciones disponibles para
un presupuesto de Odoo:

|image27|

Enviar por correo electrónico
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Seleccionado esta opción, le podremos enviar una copia del presupuesto
al mail informado en el registro del cliente. Configurar la opción de
envío de mail es una tema de un próximo capítulo.

Imprimir
^^^^^^^^

Seleccionando esta opción podremos imprimir una copia del presupuesto en
un archivo pdf.

Confirmar la venta
^^^^^^^^^^^^^^^^^^

El botón “Confirmar venta” convierte el presupuesto en un pedido de
venta y empuja la transacción hacia adelante en el workflow de ventas.

Cancelar
^^^^^^^^

Seleccionando esta opcion se nos consultará si queremos cancelar el
presupuesto. El presupuesto no será eliminado y todavía podrá ser
consultado. La cancelación de un presupuesto finaliza el workflow del
pedido de ventas y el presupuesto solo se mantendrá en el sistema con
fines de archivo.

Para continuar con nuestro ejemplo, hagamos clic en el botón “Confirmar”
para convertir el presupuesto en un pedido. Veremos que el estado del
pedido cambia de Presupuesto a Pedido de ventas.

|image28|

Facturar la venta
-----------------

Dependiendo del workflow del negocio, un montón de cosas pueden pasar
después de que confirmamos un pedido de ventas. En empresas de
manufactura (fabricación), podríamos necesitar comprar la materia prima
y crear una orden de fabricación del producto final antes de que podamos
facturar al cliente.

En nuestro ejemplo vamos a avanzar y a facturar al cliente por el pedido
del “Mouse inalamb. Genius”. Seleccionemos “Crear Factura” para generar
una factura a partir del pedido de ventas.

Se muestra un asistente de facturación de pedidos de venta para guiarnos
atravez del proceso de creación.

La siguiente captura de pantalla muestra el asistente de facturación de
pedidos:

|image29|

Que queremos facturar?
~~~~~~~~~~~~~~~~~~~~~~

Odoo provee una variedad de opciones para facturar el pedido completo o
facturar basado en otros métodos.

Las ópciones disponibles son:

Lineas a facturar (Deducir pagos anticipados)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Con esta opción podemos facturar por linea de pedido y descontar algún
pago anticipado que nos hayan realizado.

Lineas de factura
^^^^^^^^^^^^^^^^^

Igual que la opción anterior pero no se tendrán en cuenta los pagos
anticipados.

Pago anticipado (porcentaje)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Nos permite facturar un pago anticipado como un porcentaje que nos este
realizando el cliente.

Pago anticipado (cantidad fija)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Idéntico que el anterior pero en vez de un porcentaje el pago será por
una cantidad fija.

Crear la factura
~~~~~~~~~~~~~~~~

Para nuestro ejemplo usaremos la opción por defecto. Como no tenemos
pagos anticipados, Odoo procesará el pedido como si hubiesemos elegido
la primera opción “Lineas de factura”.

Seleccionar la opción “Crear y ver facturas” para generar la factura. La
factura se crea en el estado “Borrador”. Seleccionamos “Validar” para
confirmar la factura.

Si haz seguido todos los pasos y todo funcionó como debería, entonces
deberías ver una factura similar a esta:

|image30|

Breadcrumb
^^^^^^^^^^

A esta altura vale la pena observar una caracteristica de la interface
de Odoo llamada “breadcrumb” (se traduce “migas de pan”). Estos links,
que aparecen en la vista de formulario justo debajo del menú principal,
nos permiten recorrer el camino hacia atrás desde la factura al pedido
del cual deriva

|image31|

El uso de estos links es el metodo preferido para navegar hacia las
pantallas anteriores antes de usar el botón de Retroceder del navegador.

Resumen
-------

En este capítulo, comenzamos creando una base de datos de Odoo. Luego
instalamos el módulo de “Gestión de ventas” y creamos nuestro primer
cliente.

Con nuestro cliente creado, cambiamos nuestra atención a la
configuración de un producto en Odoo e ingresamos la información básica
de nuestra empresa.

Luego, creamos un presupuesto y seguimos el workflow completo hacia
confirmar el pedido de ventas y generar la factura.

En el próximo capítulo, analizaremos nuestra estrategia de ventas y que
es lo que queremos alcanzar utilizando el CRM de Odoo.

.. |image0| image:: ./media/image1.png
   :width: 5.10897in
   :height: 4.47576in
.. |image1| image:: ./media/image2.png
   :width: 4.91667in
   :height: 2.51268in
.. |image2| image:: ./media/image3.png
   :width: 5.90556in
   :height: 4.07778in
.. |image3| image:: ./media/image4.png
   :width: 5.90556in
   :height: 3.70764in
.. |image4| image:: ./media/image5.png
   :width: 4.14583in
   :height: 1.41667in
.. |image5| image:: ./media/image6.png
   :width: 5.90556in
   :height: 2.74444in
.. |image6| image:: ./media/image7.png
   :width: 5.90556in
   :height: 3.93681in
.. |image7| image:: ./media/image8.png
   :width: 3.91667in
   :height: 0.47917in
.. |image8| image:: ./media/image9.png
   :width: 5.90556in
   :height: 3.86458in
.. |image9| image:: ./media/image10.png
   :width: 5.90556in
   :height: 3.86458in
.. |image10| image:: ./media/image11.png
   :width: 5.90556in
   :height: 4.57083in
.. |image11| image:: ./media/image12.png
   :width: 4.89102in
   :height: 3.18518in
.. |image12| image:: ./media/image13.png
   :width: 5.90556in
   :height: 1.97847in
.. |image13| image:: ./media/image14.png
   :width: 5.90556in
   :height: 1.74167in
.. |image14| image:: ./media/image15.png
   :width: 5.90556in
   :height: 2.39444in
.. |image15| image:: ./media/image16.png
   :width: 5.90556in
   :height: 3.65694in
.. |image16| image:: ./media/image17.png
   :width: 5.90556in
   :height: 3.61875in
.. |image17| image:: ./media/image18.png
   :width: 5.90556in
   :height: 2.57431in
.. |image18| image:: ./media/image19.png
   :width: 3.16667in
   :height: 2.00660in
.. |image19| image:: ./media/image20.png
   :width: 5.90556in
   :height: 3.59861in
.. |image20| image:: ./media/image21.png
   :width: 5.90556in
   :height: 4.05139in
.. |image21| image:: ./media/image22.png
   :width: 5.90556in
   :height: 4.50139in
.. |image22| image:: ./media/image23.png
   :width: 3.60256in
   :height: 2.67883in
.. |image23| image:: ./media/image24.png
   :width: 3.58333in
   :height: 2.68257in
.. |image24| image:: ./media/image25.png
   :width: 3.46795in
   :height: 2.79128in
.. |image25| image:: ./media/image26.png
   :width: 5.90556in
   :height: 1.29306in
.. |image26| image:: ./media/image27.png
   :width: 4.20513in
   :height: 0.48554in
.. |image27| image:: ./media/image28.png
   :width: 4.58974in
   :height: 0.48447in
.. |image28| image:: ./media/image29.png
   :width: 4.44872in
   :height: 0.49329in
.. |image29| image:: ./media/image30.png
   :width: 5.90556in
   :height: 3.01181in
.. |image30| image:: ./media/image31.png
   :width: 5.90556in
   :height: 4.67917in
.. |image31| image:: ./media/image32.png
   :width: 5.90556in
   :height: 1.14514in
