Oracle Client
=============

Este rol permite la instalación del cliente Oracle dentro de una implementación de Composer 1.x o 2.x desplegado dentro del bucket generado durante la provisión del ambiente Composer.

Requirements
------------

- GCloud SDK >= 375.0.0
- Ansible >= 2.9
- Python 3
- Unzip
- Ansible Collections:
  - name: community.general


Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

- Ruta del bucket donde se instalarán los archivos:

```yml
gcs_bucket: "foo"
```

- URL del archivo comprimido que contiene las librerías del cliente:

```yml
url_client_installer: "https://download.oracle.com/otn_software/linux/instantclient/185000/instantclient-basic-linux.x64-18.5.0.0.0dbru.zip"
```

- Versión del cliente:

```yml
client_folder: "instantclient_18_5"
```

Dependencies
------------

Se requiere Composer desplegado y en particular el bucket asociado a este entorno.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yml
- hosts: localhost
  remote_user: root
  roles:
  - ansible-oracle-client
  vars:
    gcs_bucket: "us-east1-emplipigas-datalak-5db2e7f9-bucket" # Se puede obtener la ruta como variable de entorno con (ejemplo) => "{{ lookup('env', 'GKE_BUCKET') }}"
    url_client_installer: "https://download.oracle.com/otn_software/linux/instantclient/185000/instantclient-basic-linux.x64-18.5.0.0.0dbru.zip"
    client_folder: "instantclient_18_5"
```

Test
----

```sh
ansible-playbook tests/test.yml -i tests/inventory
```

License
-------

BSD

Author Information
------------------

Role creado para Lipigas por Marcelo Cárdenas (hackwish).
