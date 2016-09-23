=======================
Utilitarul Apache Maven
=======================

Exerciții
=========

.. _crearea-unui-proiect-maven:

Crearea unui proiect Maven model
--------------------------------

IntelliJ IDEA Community
^^^^^^^^^^^^^^^^^^^^^^^

#. Lansați IntelliJ IDEA Community (versiunea 2016.2).
#. Clic pe *File* din meniul principal, apoi clic *New > Project...*
#. În fereastra de dailog *New Project*:

   a. Selectați *Maven* în list verticală din stînga.
   #. Selectați JDK 1.8 *(1.8 java version "1.8.0_101")* în lista derulantă *Project SDK*.
   #. Treceți la pasul următorul dînd clic pe butonul *Next*.
   #. Completați *GroupId* cu *java-ee-lab*. 
   #. Completați *ArtifactId* cu *hello-world-maven-app*.
   #. Lăsați *Version* să fie *1.0-SNAPSHOT*.
   #. Treceți la pasul următorul dînd clic pe butonul *Next*.
   #. Completați *Project name:* cu *HelloWorldMavenApp*.
   #. Clic pe *Finish* și aștepți pînă cînd IDEA crează proiectul.

#. În proiectul nou creat:

   a. În colțul dreapta-jos va aparea o ferestră popup cu titlul *Maven projects need to be imported*; dați clic pe *Enable Auto-Import*.
   #. Din meniul principal *File > Project Structure...*
   #. În pagina *Project* asigurațivă că:

      i. în lista *Project SDK este aleasă opțiunea *1.8*;
      #. în lista *Project language level* este aleasă opțiunea *8 - Lambdas, type annotation etc.*

   #. Clic pe *OK*.

#. Creați prima clasă:

   a. Treceți în zona din stînga unde este afișat structura proiectului sub formă de arbore (dacă lipsește această zonă atunci din meniul principal *View > Tool Windows > Project*).
   #. Deschideți nodul *src*, apoi nodul *main*.
   #. Clic de dreapta pe *java* (de sub nodul *main*) apoi *New > Java Class*.
   #. În ferestra de dialog *Create New Class* scrieți *hwmaven.HelloWorldApp*.
   #. Veți observa că sub *java* a apărut dosarul *hwmaven*, care de fapt este pachetul *hwmaven*. 
   #. Iar sub pachet-ul *hwmaven* a apărut clasa *HelloWorldApp*.
   #. Dublu clic pe această clasă și inserați următoarea metodă

      .. code-block:: java

         public static void main(String[] args) {
             System.out.println("Hello, world!");
         }
   
6. Lansăm aplicația:

   a. Din meniul principal *Run > Edit Configurations...*
   #. Clic pe butonașul *+* și din lista de selecție alegeți *Application*. 
   #. Completați *Name* cu *HelloWorldMavenApp*.
   #. În *Main class* clic pe butonul cu *...* și in fereastră apărută alegeți *HelloWorldApp* apoi *OK*.
   #. Din meniul principal *Run > Run 'HelloWorldMavenApp'*.

Eclipse
^^^^^^^

#. Lansați Eclipse (versiunea Neon).
#. Clic pe *File* din meniul principal, apoi clic *New > Project...*
#. În fereastra de dailog *New Project*:

   a. Deschideți nodul *Maven* și selectați *Maven Project*.
   #. Treceți la pasul următorul dînd clic pe butonul *Next*.
   #. Bifați *Create a simple project (skip archetype selection)*.
   #. Treceți la pasul următorul dînd clic pe butonul *Next*.
   #. Completați *GroupId* cu *java-ee-lab*. 
   #. Completați *ArtifactId* cu *hello-world-maven-app*.
   #. Lăsați *Version* să fie *1.0-SNAPSHOT*.
   #. Completați *Name:* cu *HelloWorldMavenApp*.
   #. Clic pe *Finish* și aștepți pînă cînd Eclipse crează proiectul.

#. Creați prima clasă:

   a. Treceți în zona din stînga unde este afișat structura proiectului sub formă de arbore și alegeți pagina *Package Explorer*.
   #. Deschideți nodul *src* și clic de dreapta pe nodul *main* apoi *New > Package*.
   #. În ferestra de dialog *New Java Package* scrieți *hwmaven*.
   #. Clic dreapta pe pachetul *hwmaven* apoi *New > Class*.
   #. În ferestra de dialog *New Java Class* scrieți *HelloWorldApp*.
   #. Veți observa că sub *java* a apărut dosarul *hwmaven*, care de fapt este pachetul *hwmaven*. 
   #. Iar sub pachet-ul *hwmaven* a apărut clasa *HelloWorldApp*.
   #. Dublu clic pe această clasă și inserați următoarea metodă

      .. code-block:: java

         public static void main(String[] args) {
             System.out.println("Hello, world!");
         }
   
6. Lansăm aplicația:

   a. Din meniul principal *Run > Run*.

NetBeans
^^^^^^^^

În curînd...

Doar linia de comandă și un simplu editor de texte (în lipsa vreunui mediu de dezvoltare)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

#. Lansați orice terminal.
#. Executați:

   .. code-block:: bash

      mvn archetype:generate -DgroupId=jav-ee-lab -DartifactId=hello-world-maven-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false

#. Treceți în dosarul *hello-world-maven-app* nou creat.
#. În dosarul *src/main/java* creați dosarul *hwmaven*.
#. În dosarul *hwmaven* creați fișierul *HelloWorldApp.java* cu conținutul:

   .. code-block:: java

      package hwmaven;

      public class HelloWorldApp {
    
          public static void main(String[] args) {
              System.out.println("Hello, world!");
          }
      }

#. Compilați proiectul  

   .. code-block:: bash

      mvn compile

#. Lansăm aplicația:

   a. Fie din linia de comandă:

      .. code-block:: bash

         mvn exec:java -Dexec.mainClass=hwmaven.HelloWorldApp

   #. Fie în *pom.xml* adăugați: 

      .. code-block:: xml

         <build>
             <plugins>
                 <plugin>
                     <groupId>org.codehaus.mojo</groupId>
                     <artifactId>exec-maven-plugin</artifactId>
                     <version>1.5.0</version>
                     <configuration>
                         <mainClass>hwmaven.HelloWorldApp</mainClass>
                         <cleanupDaemonThreads>false</cleanupDaemonThreads>
                     </configuration>
                 </plugin>
             </plugins>
         </build>

      și în linia de comandă rulați doar:

      .. code-block:: bash

         mvn exec:java -Dexec.mainClass=hwmaven.HelloWorldApp
