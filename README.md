# proyecto_final
proyecto_final_curso
 
 *Autor* Edgar Vazquez Ramirez

 ## Descripcion 
• 1986: Inicio del proyecto POTGRES
• 1996: Renombramiento a PostgreSQL 6.0
• 2005: Lanzamiento de PostgreSQL 8.0 (soporte nativo para Windows)
• 2010: PostgreSQL 9.0 (replicación streaming, Hot Standby)
• 2016: PostgreSQL 9.6 (mejoras en paralelización de consultas)
• 2020: PostgreSQL 13 (optimización de índices, nuevas características de seguridad)

## 1.- Obtención de datos

![img](./imagenes/Tiempo.jpg)

 Diseño de la base de datos

 La siginte base de datos esta diseñada para verificar algunas marcas de vehiculos con diferentes tipo de combustible que tipo de frenos tiene o tipo de traccion. 

```sql
CREATE TABLE IF NOT EXISTS public.cat_marca
(
    id_marca serial NOT NULL,
    marca character varying(50) NOT NULL,
    PRIMARY KEY (id_marca)
);

CREATE TABLE IF NOT EXISTS public.cat_tipo_motor
(
    id_tipo_motor serial NOT NULL,
    tipo_motor character varying(50) NOT NULL,
    PRIMARY KEY (id_tipo_motor)
);

CREATE TABLE IF NOT EXISTS public.tbl_autos
(
    id_autos serial NOT NULL,
    id_tipo_motor integer NOT NULL,
    id_numero_cilindro integer NOT NULL,
    id_traccion integer NOT NULL,
    id_frenos_delanteros integer NOT NULL,
    id_frenos_traseros integer NOT NULL,
    id_marca integer NOT NULL,
    PRIMARY KEY (id_marca)
);

CREATE TABLE IF NOT EXISTS public.cat_numero_cilindro
(
    id_numero_cilindro serial NOT NULL,
    numero_cilindro integer NOT NULL,
    PRIMARY KEY (id_numero_cilindro)
);

CREATE TABLE IF NOT EXISTS public.cat_traccion
(
    id_tipo_traccion serial NOT NULL,
    traccion character varying(50) NOT NULL,
    PRIMARY KEY (id_tipo_traccion)
);

CREATE TABLE IF NOT EXISTS public.cat_frenos_delanteros
(
    id_frenos_delanteros serial NOT NULL,
    frenos_delanteros character varying(50) NOT NULL,
    PRIMARY KEY (id_frenos_delanteros)
);

CREATE TABLE IF NOT EXISTS public.cat_frenos_traseros
(
    id_frenos_traseros serial NOT NULL,
    frenos_traseros character varying(50) NOT NULL,
    PRIMARY KEY (id_frenos_traseros)
);

ALTER TABLE IF EXISTS public.tbl_autos
    ADD FOREIGN KEY (id_tipo_motor)
    REFERENCES public.cat_tipo_motor (id_tipo_motor) MATCH SIMPLE
    ON UPDATE NO ACTION
    ON DELETE NO ACTION
    NOT VALID;


ALTER TABLE IF EXISTS public.tbl_autos
    ADD FOREIGN KEY (id_numero_cilindro)
    REFERENCES public.cat_numero_cilindro (id_numero_cilindro) MATCH SIMPLE
    ON UPDATE NO ACTION
    ON DELETE NO ACTION
    NOT VALID;


ALTER TABLE IF EXISTS public.tbl_autos
    ADD FOREIGN KEY (id_traccion)
    REFERENCES public.cat_traccion (id_tipo_traccion) MATCH SIMPLE
    ON UPDATE NO ACTION
    ON DELETE NO ACTION
    NOT VALID;


ALTER TABLE IF EXISTS public.tbl_autos
    ADD FOREIGN KEY (id_frenos_delanteros)
    REFERENCES public.cat_frenos_delanteros (id_frenos_delanteros) MATCH SIMPLE
    ON UPDATE NO ACTION
    ON DELETE NO ACTION
    NOT VALID;


ALTER TABLE IF EXISTS public.tbl_autos
    ADD FOREIGN KEY (id_frenos_traseros)
    REFERENCES public.cat_frenos_traseros (id_frenos_traseros) MATCH SIMPLE
    ON UPDATE NO ACTION
    ON DELETE NO ACTION
    NOT VALID;


ALTER TABLE IF EXISTS public.tbl_autos
    ADD FOREIGN KEY (id_marca)
    REFERENCES public.cat_marca (id_marca) MATCH SIMPLE
    ON UPDATE NO ACTION
    ON DELETE NO ACTION
    NOT VALID;

END;
```

 ## Configuración del entorno SQL

 
Comandos básicos y avanzados
Aperendi en clase a crear una tabla desde SQL Shell
 ![img](./imagenes/Captura%20de%20pantalla%202024-06-17%20115303.png)

## Diseño de la base de datos

# 1.- Modelado de Datos

* Modelo Conceptual:

El diagrama de entidad-relación (DER) 
Define las entidades, atributos y relaciones.
 Por ejemplo:
Entidades: Cliente, Producto, Pedido.
Atributos: ID, Nombre, Precio.
Relaciones: Cliente realiza Pedido, Pedido contiene Producto.

* Modelo Lógico:
Traduce el modelo conceptual a un modelo lógico utilizando el modelo relacional.
Define tablas, claves primarias y foráneas.
Normaliza las tablas para evitar redundancia y anomalías.


* Modelo Físico:
Decide sobre el motor de base de datos (PostgreSQL).
Crea las tablas en SQL con las columnas y restricciones adecuadas.

* Integridad y Seguridad:
Agrega restricciones de integridad (claves primarias, foráneas, restricciones UNIQUE, etc.).
Define permisos de acceso para usuarios y roles.
# 2.- Relaciones y Llaves

Llaves primarias y foráneas

1.- Llave Primaria (Primary Key):

* Es un campo o conjunto de campos en una tabla que identifica de manera única cada registro.
* Garantiza que no haya duplicados y permite un acceso rápido a los datos.
* Por ejemplo, en una tabla de “Clientes”, el campo “ID de cliente” podría ser la llave primaria.

2.- Llave Foránea (Foreign Key):
* La llave foránea es un campo en una tabla que se relaciona con la llave primaria de otra tabla.
* Establece una conexión entre dos tablas, permitiendo consultas y operaciones relacionales.
* Por ejemplo, en una tabla de “Pedidos”, el campo “ID de cliente” podría ser una llave foránea que se relaciona con la tabla de “Clientes”.

## 3.- Indices y Vistas

# Tipos de índices y su uso

1.- Índices (Indexes):
* Los índices son estructuras que mejoran la velocidad de las consultas en una tabla.
* Para crear un índice en PostgreSQL, puedes usar la sentencia CREATE INDEX.
* Existen varios tipos de índices, como 

- B-tree: (ARBOL):
- Hash, 
- GiST  
- GIN, 
cada uno adaptado a diferentes tipos de consultas.

Creación y uso de vistas

 ![img](./imagenes/proyecto.pgerd.png)
 ![img](./imagenes/creacion%20de%20tablas.png)

 
 ## Gestión de usuarios
 los términos “usuarios”, “grupos” y “roles” los usuarios tienen permiso para iniciar sesión de forma predeterminada "superusuario".
Puedes crear un usuario utilizando la siguiente instrucción SQL:
Creamos un usario, debemos estar conectados como super usario para poder dar privilegios, ponemos el nombre del usario que queremos crear. 

 ![img](./imagenes/crear%20roles%20.png)

 ![img](./imagenes/ponemos%20contraseña%20al%20rol.png)

   ![img](./imagenes/privilegios%20de%20roles.png)






 ## Creando una copia de seguridad



 ## Optimizando consultas




 ## Preparando un proceso de réplica y alta disponibilidad



 ## Preparando el monitoreo



 ## Migración de datos





 ## Presentación del proyecto




