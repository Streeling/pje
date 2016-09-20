=======================
Utilitarul Apache Maven
=======================

Exerciții
=========

Crearea unui proiect Maven model
--------------------------------

IntelliJ IDEA (Ediția Community) 
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

#. Lansați IntelliJ IDEA Community (versiunea 2016.2).
#. Clic pe *File* din meniul principal, apoi clic *New -> Project...*
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
   #. Din meniul principal *File -> Project Structure...*
   #. În pagina *Project* asigurațivă că:

      i. în lista *Project SDK este aleasă opțiunea *1.8*;
      #. în lista *Project language level* este aleasă opțiunea *8 - Lambdas, type annotation etc.*

   #. Clic pe *OK*.

#. Creați prima clasă:

   a. Treceți în zona din stînga unde este afișat structura proiectului sub formă de arbore (dacă lipsește această zonă atunci din meniul principal *View -> Tool Windows -> Project*).
   #. Deschideți nodul *src*, apoi nodul *main*.
   #. Clic de dreapta pe *java* (de sub nodul *main*) apoi *New -> Java Class*.
   #. În ferestra de dialog *Create New Class* scrieți *hwmaven.HelloWorldApp*.
   #. Veți observa că sub *java* a apărut dosarul *hwmaven*, care de fapt este pachetul *hwmaven*. 
   #. Iar sub pachet-ul *hwmaven* a apărut clasa *HelloWorldApp*.
   #. Dublu clic pe această clasă și inserați următoarea metodă::
.. code-block:: java

   public static void main(String[] args) {
     System.out.println("Hello, world!");
   }
6. Lansăm aplicația:

   a. Din meniul principal *Run -> Edit Configurations...*
   #. Clic pe butonașul *+* și din lista de selecție alegeți *Application*. 
   #. Completați *Name* cu *HelloWorldMavenApp*.
   #. În *Main class* clic pe butonul cu *...* și in fereastră apărută alegeți *HelloWorldApp* apoi *OK*.
   #. Clic pe *OK*.
   # Din meniul principal *Run -> Run 'HelloWorldMavenApp'*.

Eclipse XXX 
^^^^^^^^^^^

#. în *Eclipse*, meniul *File---> New ---> Other*;
#. se selectează *Maven ---> Maven Project ---> Next*;
#. se bifează *Use default Workspace location*;
#. se selectează *All Catalog* şi din listă maven-archetype-quickstart;
#. se completează *Group Id* (se va folosi id-ului userului de pe domeniul SCS);
#. se completează *Artefact Id* (se va folosi id-ului userului de pe domeniul SCS);
#. câmpul *Package* se va completa automat;
  #. nu se va modifica, dar va fi folosit în cadrul proiectului Maven;
#. *Finish* pentru a finaliza crearea proiectului Maven.

NetBeans
^^^^^^^^

#. în *Eclipse*, meniul *File---> New ---> Other*;
#. se selectează *Maven ---> Maven Project ---> Next*;
#. se bifează *Use default Workspace location*;
#. se selectează *All Catalog* şi din listă maven-archetype-quickstart;
#. se completează *Group Id* (se va folosi id-ului userului de pe domeniul SCS);
#. se completează *Artefact Id* (se va folosi id-ului userului de pe domeniul SCS);
#. câmpul *Package* se va completa automat;
  #. nu se va modifica, dar va fi folosit în cadrul proiectului Maven;
#. *Finish* pentru a finaliza crearea proiectului Maven.
