===========
Servlet-uri
===========

Anatomia unui servlet
=====================

Ciclul de viaţă al unui servlet
===============================

Recepționarea și prelucrarea cererii HTTP
=========================================

Formarea raspunsului HTTP
=========================

Exerciții
=========

Crearea unui proiect web model bazat pe servlet-uri
---------------------------------------------------

#. :ref:`Creați un proiect Maven <crearea-unui-proiect-maven>` cu numele *HelloWorldServletApp*.
#. Deschideți fișierul *pom.xml* și: 
   
   a. Modificați `tipul de împachetare <https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html#Packaging>`_ să fie *war*.
   #. Adăugați dependința pentru `Java Servlet API 3.1.0 <https://mvnrepository.com/artifact/javax.servlet/javax.servlet-api/3.1.0>`_.

#. Creați prima clasă servlet:
   
   a. În dosarul *src/main/java* creați pachetul *hwservlet*.
   #. În cadrul acestui pachet creați clasa *HelloWorldServlet* care moștenește clasa `HttpServlet <https://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServlet.html>`_.
   #. În clasa *HelloWorldServlet* suprascrieți metoda `doGet <https://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServlet.html#doGet-javax.servlet.http.HttpServletRequest-javax.servlet.http.HttpServletResponse->`_ în felul următor:
   
      .. code-block:: java

         // Set response content type
         response.setContentType("text/html");

         // Generate page content
         PrintWriter out = response.getWriter();
	     out.println("<html><body>");
         out.println("<h1>Hello, World!</h1>");
         out.println("</body></html>");	  

#. Creați descriptorul de instalare:		 
		 
   #. În dosarul *src/main/* creați dosarul *webapp* împreuna cu subdosarul *WEB-INF*.
   #. În dosarul *src/main/webapp/WEB-INF* creați fișierul *web.xml* cu următorul conținut:

      .. code-block:: xml
      
         <web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
            xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
            xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
	    	http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd"
            version="3.1">
         </web-app>   
	  
   #. În acest fișier:

      .. code-block:: xml
      
         <servlet>
           <servlet-name>HelloWorld</servlet-name>
           <servlet-class>hwservlet.HelloWorldServlet</servlet-class>
         </servlet>

         <servlet-mapping>
           <servlet-name>HelloWorld</servlet-name>
           <url-pattern>/</url-pattern>
         </servlet-mapping>

Rularea unui proiect web model bazat pe servlet-uri
---------------------------------------------------

IntelliJ IDEA Community
^^^^^^^^^^^^^^^^^^^^^^^

#. :ref:`Instalați plugin-ul <instalare-plugin-intellij-idea>` IDEA Jetty Runner.
#. Din meniul principal *Run > Edit Configurations...*
#. Clic pe butonașul *+* și din lista de selecție alegeți *Jetty Runner*.
#. Completați *Name* cu *HelloWorldServletApp*.
#. Din meniul principal *Run > Run 'HelloWorldServletApp'*.
#. În navigator (Firefox, Google Chrome etc) accesați adresa *localhost:8080*.


Eclipse
^^^^^^^

În curînd...

Dinamic
-------

Modificați *HelloWorldServlet* astfel încît mai jos de 

.. code-block:: html
   
   <h1>Hello, World!</h1>
   
să afișeze data și ora curentă înuntrul perechii de tag-uri *<h2>...</h2>*.

Lista
-----

Avem o listă de obiecte de tip X afișați aceste obiecet în *<ul></ul>*.