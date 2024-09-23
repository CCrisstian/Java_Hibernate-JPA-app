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
<p>Hibernate también permite ejecutar consultas <b>SQL nativas</b> directamente, lo que es útil cuando se requieren operaciones complejas o específicas a nivel de base de datos que no pueden realizarse fácilmente con HQL o Criteria API. Las consultas nativas trabajan directamente con las tablas de la base de datos, por lo que se pierde el mapeo objeto-relacional en estos casos.</p>

<h1 align="center">Clase Entidad</h1>
<p>Una <b>clase entidad</b> en el contexto de <b>Java con Hibernate (o JPA - Java Persistence API)</b> es una clase de Java que está mapeada a una tabla de base de datos. Las instancias de esta clase representan filas de la tabla, y los atributos de la clase corresponden a las columnas de la tabla. Hibernate utiliza estas clases para realizar el mapeo objeto-relacional (ORM), es decir, para convertir entre los objetos de Java y los registros de la base de datos.</p>

```java
@Entity
public class Cliente {
    
    @Id
    private Long id;

    private String nombre;

    private String apellido;

    @Column(name = "forma_pago")
    private Date formaPago;

    // Getters y setters
}
```

- `@Entity`:
  - La anotación `@Entity` indica que esta clase de Java es una entidad y que estará mapeada a una tabla en la base de datos. Hibernate la utilizará para realizar el mapeo.
  - Hibernate creará o utilizará una tabla (con el nombre de la clase `Cliente`, a menos que se especifique otro nombre con `@Table`) que tendrá las columnas correspondientes a los atributos de la clase.
- `@Id`:
  - `@Id` marca el atributo `id` como la clave primaria de la entidad. Este campo será el identificador único de cada instancia de la clase `Cliente` en la base de datos.
- Atributos (`nombre`, `apellido`, `formaPago`):
  - Los atributos `nombre` y `apellido` se mapearán a columnas en la tabla correspondiente a la entidad `Cliente`. Por defecto, el nombre de la columna será el mismo que el nombre del atributo.
- `@Column(name = "forma_pago")`:
  - La anotación `@Column` se usa para personalizar el mapeo de un atributo de la entidad a una columna en la base de datos. En este caso, el atributo `formaPago` se mapeará a una columna llamada `forma_pago` en lugar de usar el nombre por defecto del campo (`formaPago`).
- <b>Getters y Setters</b>:
  - Los getters y setters son métodos necesarios para que Hibernate pueda acceder y modificar los valores de los atributos. Hibernate utiliza estos métodos para leer y escribir los datos de los objetos en la base de datos.

<h1 align="center">Asociaciones: @ManyToOne, @OneToMany, @OneToOne, @ManyToMany</h1>
<p>En Hibernate y JPA, las asociaciones o relaciones entre entidades permiten modelar cómo las clases Java (entidades) se relacionan entre sí, reflejando las relaciones entre tablas de la base de datos. A continuación, se explican los tipos más comunes de asociaciones:</p>

<h2>@ManyToOne (Muchos a Uno)</h2>

- Esta asociación indica que muchas instancias de una entidad están relacionadas con una instancia de otra entidad.
- Se representa con una clave foránea en la tabla de la entidad "muchos".

<h2>@OneToMany (Uno a Muchos)</h2>

- Representa una relación donde <b>una</b> instancia de una entidad está relacionada con <b>muchas</b> instancias de otra entidad.
- Es el inverso de la relación `@ManyToOne` y generalmente se mapea junto con esta.

<h2>@OneToOne (Uno a Uno)</h2>

- Define una relación donde <b>una</b> instancia de una entidad está relacionada con una <b>sola</b> instancia de otra entidad.
- Esta relación suele utilizarse cuando una tabla tiene una dependencia de uno a uno con otra tabla.

<h2>@ManyToMany (Muchos a Muchos)</h2>

- Define una relación donde <b>muchas</b> instancias de una entidad están relacionadas con <b>muchas</b> instancias de otra entidad.
- Normalmente, esto se mapea con una tabla intermedia que contiene las claves foráneas de ambas tablas.
