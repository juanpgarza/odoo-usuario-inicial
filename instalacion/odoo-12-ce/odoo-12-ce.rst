######################################################
Instalación de Odoo 12 en Docker
######################################################

Los siguientes pasos indican como crear un entorno para ejecutar Odoo 12 en docker.

El tutorial esta verificado en una máquina virtual linux Ubuntu 16.04 server.
Igualmente, debería funcionar correctamente en cualquier distribución de linux con docker 
(y docker composer) instalados.

1.  **Instalar docker** 

Tutorial para instalar docker en ubuntu 16.04 y 18.04:

https://docs.docker.com/install/linux/docker-ce/ubuntu/

2.  **Instalar docker-compose** 

Tutorial para instalar docker compose:

https://docs.docker.com/compose/install/

3.  **Clonar repositorio odoo-dev de github** 

.. code-block:: console

   $ cd ~ 
   $ git clone https://github.com/juanpgarza/odoo-dev.git

Nota: si ya tenes la estructura odoo-dev creada, deberás ejecutar:

.. code-block:: console

   $ cd ~/odoo-dev/ 
   $ git pull

4.  **Clonar repositorio de Odoo 12** 

.. code-block:: console

   $ cd 12/proyecto1
   $ sudo mkdir src/
   $ cd src/
   $ sudo git clone https://github.com/odoo/odoo.git --branch 12.0 --depth 1 --single-branch .

6.  **Generar la imagen de docker** 

.. code-block:: console

   $ cd ~/odoo-dev/12/proyecto1
   $ docker build -t img_odoo_12 .

7.  **Copiar archivo de configuración de Odoo** 

.. code-block:: console

   $ cp .odoorc src/

8.  **Levantar contenedores de Odoo** 

.. code-block:: console

   $ cd ~/odoo-dev/12/proyecto1
   $ docker-compose up -d

Ahora ya podemos acceder a Odoo desde:

http://ip-maquina-virtual:8069

La primera vez que se invoca esta url, tomará un tiempo para que termine de cargar la página de inicio.
Esto es porque se crea una base de datos inicial llamada odoo.

9.  **Consultar el log de Odoo** 

.. code-block:: console

   $ docker ps
   $ docker logs -f cont_odoo_12-proy1

