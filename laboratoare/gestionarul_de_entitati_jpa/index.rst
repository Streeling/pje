==========================
Getionarul de entități JPA
==========================



EntityManager
-------------

#. :ref:`Creați un proiect Maven <crearea-unui-proiect-maven>` cu numele *FruitManager*.
#. În dosarul *src/main/java* creați pachetul *fruitmgr*.
#. În cadrul acestui pachet creați clasa *FruitManagerApp*.
#. În cadrul pachetului *fruitmgr* creați subpachetul *domain*.
#. În cadrul pachetului *domain* creați clasa *Fruit*.
#. Deschideți fișierul *pom.xml* șî adăugați dependința pentru Hibernate EntityManager:

   .. code-block:: xml

      <!-- https://mvnrepository.com/artifact/org.hibernate/hibernate-entitymanager -->
      <dependency>
          <groupId>org.hibernate</groupId>
          <artifactId>hibernate-entitymanager</artifactId>
          <version>5.2.2.Final</version>
      </dependency>

#. Treceți in clasa *Fruit* și aplicați pe aceasta adnotarea :code:`@Entity` (:code:`javax.persistence`).
#. Adăugați 3 atribute :code:`private` la această clasă:

   a. *id* de tip :code:`Long`.
   #. *name* de tip :code:`String`.
   #. *price* de tip :code:`BigDecimal`.

#. Pentru fiecare dintre aceste atribute creați metodele getter și setter.

   a. În IDEA puneți cursorul pe clasă, clic de dreapta și alegeți *Generate... > Getter and Setter*.
   #. În Eclipse puneți cursorul pe clasă, clic de dreapta și alegeți *Source > Generate Getters and Setters...*.

#. Pe metoda getter pentru atributul *id* aplicați adnotările:

   .. code-block:: java

      @Id
      @GeneratedValue

#. În dosarul *resources* adăugați fișierul *META-INF/persistence.xml* (clic dreapta pe *resources* și *New > File*) cu următorul conținut:

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

#. În dosarul *resources* adăugați fișierul *hibernate.properties* cu următorul conținut:

   .. code-block:: properties

      hibernate.dialect=org.hibernate.dialect.H2Dialect
      hibernate.connection.url=jdbc:h2:file:./target/h2db/db/fruitmgr
      hibernate.connection.driver_class=org.h2.Driver
      hibernate.connection.password=sa
      hibernate.connection.username=
      hibernate.hbm2ddl.auto=update
      hibernate.show_sql=true
      hibernate.format_sql=true

#. Treceți la fișierul *pom.xml* și adăugați dependința pentru baza de date H2 (http://www.h2database.com/):

   .. code-block:: xml

      <!-- https://mvnrepository.com/artifact/com.h2database/h2 -->
      <dependency>
          <groupId>com.h2database</groupId>
          <artifactId>h2</artifactId>
          <version>1.4.192</version>
      </dependency>


#. Treceți în clasa *FruitManagerApp* și adăugați metoda :code:`main`:

   .. code-block:: java

      public static void main(String[] args) {
          EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("fruits");
          EntityManager entityManager = entityManagerFactory.createEntityManager();

          Fruit fruit = new Fruit();
          fruit.setName("Mere (kg)");
          fruit.setPrice(BigDecimal.valueOf(14.95));
          entityManager.persist(fruit);

          fruit = new Fruit();
          fruit.setName("Avocado (buc)");
          fruit.setPrice(BigDecimal.valueOf(12.45));
          entityManager.persist(fruit);

          entityManager.close();
          entityManagerFactory.close();
      }

#. Rulați programul! Dacă ultimul rînd din cele afișate de program va fi:

   .. code-block:: bash

      Process finished with exit code 0

   atunci totul e ok.

#. Treceți în clasa *FruitManagerApp* și înlocuiți metoda :code:`main`: cu

   .. code-block:: java

      public static void main(String[] args) {
          EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("fruits");
          EntityManager entityManager = entityManagerFactory.createEntityManager();

          Fruit fruit = new Fruit();
          fruit.setName("Mere (kg)");
          fruit.setPrice(BigDecimal.valueOf(14.95));
          entityManager.persist(fruit);

          fruit = new Fruit();
          fruit.setName("Avocado (buc)");
          fruit.setPrice(BigDecimal.valueOf(12.45));
          entityManager.persist(fruit);

          entityManager.close();
          entityManagerFactory.close();
      }

#. Rulați aplicația! Trebuie să fie afișat lista fructelor introduse recent în baza de date.


DBeaver
-------

EntityManager2
--------------

#. Să nu fie mai multe produse cu același nume.
#. Adugați un atribut pentru a păstra data expirării.

EntityManager2
--------------

#. Adăugați o nouă entitate pentru unitatea de măsură.
#. Adăugați o nouă entitate pentru țara de proveniență.
