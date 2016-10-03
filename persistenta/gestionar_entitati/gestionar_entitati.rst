===========================================
Gestionarul de entități JPA (EntityManager)
===========================================

Exerciții
=========

EntityManager
-------------

#. :ref:`Creați un proiect Maven <crearea-unui-proiect-maven>` cu numele *PlacesApp*.
#. În dosarul *src/main/java* creați pachetul *places*.
#. În cadrul acestui pachet creați clasa *PlacesApp*.
#. În cadrul pachetului *places* creați subpachetul *domain*.
#. În cadrul pachetului *domain* creați clasa *Place*.
#. Deschideți fișierul *pom.xml* șî adăugați dependința pentru `Hibernate EntityManager <https://mvnrepository.com/artifact/org.hibernate/hibernate-entitymanager/5.2.2.Final>`_.
#. Treceți in clasa *Place* și aplicați pe aceasta adnotarea :code:`@Entity` (din pachetul :code:`javax.persistence`).
#. Adăugați 3 atribute :code:`private` la această clasă:

   a. *id* de tip :code:`Long`.
   #. *name* de tip :code:`String`.
   #. *address* de tip :code:`String`.

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
          <persistence-unit name="places" transaction-type="RESOURCE_LOCAL">
              <provider>org.hibernate.jpa.HibernatePersistenceProvider</provider>
              <class>places.domain.Place</class>
          </persistence-unit>
      </persistence>

#. În dosarul *resources* adăugați fișierul *hibernate.properties* cu următorul conținut:

   .. code-block:: properties

      hibernate.dialect=org.hibernate.dialect.H2Dialect
      hibernate.connection.url=jdbc:h2:file:./target/h2db/db/places
      hibernate.connection.driver_class=org.h2.Driver
      hibernate.connection.password=sa
      hibernate.connection.username=
      hibernate.hbm2ddl.auto=update
      hibernate.show_sql=true
      hibernate.format_sql=true

#. Treceți la fișierul *pom.xml* și adăugați dependința pentru `baza de date H2 <https://mvnrepository.com/artifact/com.h2database/h2/1.4.192>`_ (http://www.h2database.com/):
#. Treceți în clasa *PlacesApp* și adăugați metoda :code:`main`:

   .. code-block:: java

      public static void main(String[] args) {
          EntityManagerFactory entityManagerFactory = Persistence.createEntityManagerFactory("fruits");
          EntityManager entityManager = entityManagerFactory.createEntityManager();

          Place place = new Place();
          place.setName("Universitatea de Stat „A. Russo” din Bălți");
          place.setAddress("m. Balți, str. Pușkin 38");
          entityManager.persist(place);

          place = new Place();
          place.setName("Moldova-Agroindbank filiala Bălți");
          place.setAddress("m. Balți, str. Pușkin 56/a");
          entityManager.persist(place);
          
          entityManager.close();
          entityManagerFactory.close();
      }

#. Rulați programul! Dacă ultimul rînd din cele afișate de program va fi:

   .. code-block:: bash

      Process finished with exit code 0

   atunci totul e ok.

DBeaver
-------

EntityManager2
--------------

#. Să nu fie mai multe locuri cu același nume.
#. Adugați 2 atribut pentru a păstra latitudinea și longitudinea.
