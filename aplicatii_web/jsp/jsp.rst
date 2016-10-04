==========
Pagini JSP
==========

Directive de pagină
===================

Expression Language (EL)
========================

Biblioteci de tag-uri
=====================

Exerciții
=========

.. _creare-servlet-jsp:

Crearea unui proiect web model bazat pe servlet-uri și JSP
----------------------------------------------------------

#. :ref:`Creați un Servlet <creare-servlet>` cu numele *FruitShop*.
#. Creați clasa servlet :code:`HomeServlet`. 
#. În dosarul *webapp/WEB-INF* creați dosarul *pages*.
#. În acest dosar adăugați fișierul *home.jsp*:

   .. code-block:: html
   
      <html>
      <body>
      <h1>First app</h1>
      <h2>Hello ${username}</h2>
      </body>
      </html>
   
#. În servlet

   .. code-block:: javae
   
      request.setAttribute("username", "Student");
      getServletContext().getRequestDispatcher("/WEB-INF/pages/home.jsp").forward(request, response);   
      
22
--

#. Creați PlacesDao
#. Creați beans.xmln

33
--

Creați formular pentru adăugare/modificare Place

44
--

Creați formular pentru căutare

