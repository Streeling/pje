=========
Hibernate
=========

Exerciții
=========

EntityManager
-------------

#. Lansați IntelliJ IDEA Community.
#. Creați un proiect Maven cu numele FruitManager.
#. În dosarul *src* creați pachetul *fruitmgr*.
#. În cadrul acestui pachet creați clasa *FruitManagerApp*.
#. În cadrul pachetului *fruitmgr* creați subpachetul *domain*.
#. În cadrul pachetului *domain* creați clasa *Fruit*.
#. Deschideți *pom.xml* șî adăugati dependințele
.. code-block:: xml

    <dependencies>
        <!-- https://mvnrepository.com/artifact/org.hibernate/hibernate-core -->
        <dependency>
            <groupId>org.hibernate</groupId>
            <artifactId>hibernate-core</artifactId>
            <version>5.2.2.Final</version>
        </dependency>
    </dependencies>

#. Treceți in clasa *Fruit* și adăugați deasupra clasei adnotarea :code:`@Entity`, imediat IDEA vă va propune o listă de pache de unde s-o importați alegeți :code:`javax.persistence`.
#. Adăugați 3 atribute :code:`private` la această clasă:
   a. *id* de tip :code:`Long`.
   #. *name* de tip :code:`String`.
   #. *price* de tip :code:`BigDecimal`.
#. Puneți cursorul pe clasă, clic de dreapta și alegeți *Generate... -> Getter and Setter*.
#. În ferestra de dialog alegeți toate trei atribute și *OK*. 
#. Pe getterul :code:`getId()` puneți adnotările:
.. code-block:: java

   @Id
   @GeneratedValue

#. În dosarul *resources* adăugați fișierul *META-INF/persistence.xml*.
.. code-block:: xml

   <?xml version="1.0" encoding="UTF-8" ?>
   <persistence xmlns="http://xmlns.jcp.org/xml/ns/persistence"
                xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/persistence
                http://xmlns.jcp.org/xml/ns/persistence/persistence_2_1.xsd"
                version="2.1">
       <persistence-unit name="fruits" transaction-type="RESOURCE_LOCAL">
           <provider>org.hibernate.jpa.HibernatePersistenceProvider</provider>
           <class>fruitmgr.domain</class>
       </persistence-unit>
   </persistence>
#. *hibernate.properties*
.. code-block:: propertries

   hibernate.dialect=org.hibernate.dialect.H2Dialect
   hibernate.connection.url=jdbc:h2:~/xxxxxxxxxxx
   hibernate.connection.driver_class=org.h2.Driver
   hibernate.connection.password=sa
   hibernate.connection.username=
   hibernate.hbm2ddl.auto=update
   hibernate.show_sql=false
   hibernate.format_sql=true
   hibernate.jdbc.batch_size=0

