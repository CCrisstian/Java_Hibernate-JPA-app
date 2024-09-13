<h1 align="center">Hibernate</h1>
<p>Hibernate es una herramienta de <b>mapeo objeto-relacional</b> (<b>ORM</b>) para Java que permite a los desarrolladores interactuar con bases de datos utilizando objetos en lugar de SQL directo. Simplifica las operaciones de base de datos al traducir automáticamente las clases Java a tablas y las instancias de clases a registros, facilitando la persistencia de datos sin escribir consultas SQL manuales.</p>
<p align="center"><img width="700" alt="image" src="https://github.com/user-attachments/assets/f1732051-8a96-40b3-bb64-0990fbd48a11"></p>

- <b>Repositorio / DAO (Data Access Object)</b>: Es la capa de abstracción que maneja las operaciones de persistencia y recuperación de datos. Aquí es donde se definen las consultas y operaciones CRUD que interactúan con las entidades de la base de datos.
- <b>Java Persistence API (JPA)</b>: Es una especificación estándar de Java para manejar la persistencia de objetos. JPA define un conjunto de anotaciones y API para gestionar entidades y mapeo objeto-relacional. Hibernate puede implementarse utilizando JPA como una capa de abstracción adicional para gestionar las entidades.
- <b>Hibernate Native API<b/>: Es la API propia de Hibernate, que proporciona características adicionales que no están disponibles en JPA. Los desarrolladores pueden optar por usar esta API cuando necesiten funcionalidades específicas de Hibernate.
- <b>Hibernate</b>: Es el motor ORM que hace la traducción entre las clases Java y las tablas de la base de datos. Hibernate administra las transacciones, el mapeo y las consultas SQL de forma automática.
- <b>JDBC (Java Database Connectivity)</b>: Es la API estándar de Java para conectarse a bases de datos. Hibernate se basa en JDBC para ejecutar las consultas SQL y comunicarse con la base de datos, pero abstrae la complejidad de esta interacción para los desarrolladores.

<p align="center"><img width="700" alt="image" src="https://github.com/user-attachments/assets/e1109b3b-43f5-4480-afb4-404b394f6a60"></p>

- <b>los objetos "entities" (entidades)</b>: son clases de Java que representan tablas en una base de datos relacional. Cada instancia de una entidad corresponde a una fila en la tabla, y los atributos de la clase representan las columnas de esa tabla.

<h1 align="center">Tipos de consultas</h1>
<h2>Hibernate Query Language (HQL)</h2>
<p><b>HQL</b> es un lenguaje de consulta orientado a objetos que se parece mucho al SQL, pero está diseñado para trabajar con entidades en lugar de tablas y columnas. Las consultas HQL permiten trabajar directamente con las entidades de Java en lugar de con las tablas relacionales, lo que facilita la manipulación de datos en un entorno orientado a objetos.</p>
<h2>Criteria API</h2>
<p><b>Criteria API</b> es una API de Hibernate que permite construir consultas de manera programática. Esto resulta útil cuando las consultas son dinámicas o se basan en varias condiciones que se conocen en tiempo de ejecución. Este enfoque es muy flexible y evita tener que escribir consultas en cadena de texto.</p>
<h2>Sql Nativo</h2>
