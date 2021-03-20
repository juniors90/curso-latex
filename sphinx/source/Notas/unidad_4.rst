Textos e Hipertextos
=====================

Etiquetas y referencias cruzadas.
---------------------------------------------------------

El paquete se deriva y se basa en el trabajo del proyecto :math:`Hyper\TeX{}`, descrito en `hypertex <http://xxx.lanl.gov/hypertex/1>`_. Amplía la funcionalidad de todos los comandos de referencias cruzadas de :math:`\LaTeX{}` (incluida la tabla de contenido, bibliografías, etc.) para producir comandos especiales que un controlador puede convertir en enlaces de hipertexto; también proporciona nuevos comandos para permitir al usuario escribir enlaces de hipertexto *ad hoc*, incluidos aquellos a documentos externos y URLs.

Estructura básico
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
 Hay que añadir en el preámbulo: 
 
.. code-block:: latex
    :caption: hyperref.tex
    :name: hyperref-tex
    :linenos:
    
    \usepackage{hyperref}

Asegúrese de que sea el último de sus paquetes cargados, para darle la posibilidad de que no se sobrescriba, ya que su trabajo es redefinir muchos comandos :math:`\LaTeX{}`. Con suerte, encontrará que todas las referencias cruzadas funcionan correctamente como hipertexto. Por ejemplo, los comandos ``\section`` producirán un marcador y un enlace, mientras que los comandos ``\section*{}`` solo mostrarán enlaces cuando se combinen con un comando ``\addcontentsline`` correspondiente.

Otras opciones controlan la apariencia de los enlaces y brindan un control adicional sobre la salida **PDF**. Por ejemplo, ``colorlinks``, como bien indica su nombre, colorea los enlaces en lugar de usar recuadros.


Hiperlinks
~~~~~~~~~~~~~~~~~~~~~~~~~~

Si necesita hacer referencias a URL o escribir enlaces explícitos, se proporcionan las siguientes macros de usuario de bajo nivel:

.. code-block:: latex
    :caption: hyiperlinks.tex
    :name: hiperlinks-tex
    :linenos:
    
    \url{URL}

En el caso de agregar texto y se convierta en un hipervínculo a la URL, donde debe ser una URL completa (relativa a la URL base, si está definida) se utiliza el siguiente comando 

.. code-block:: latex
    :caption: URL.tex
    :name: URL-tex
    :linenos:
    
    \href{URL}{texto}

Los caracteres especiales ``#`` y ``~`` no necesitan escaparse de ninguna manera (a menos que el comando se use en el argumento de otro comando).

.. code-block:: latex
    :caption: url_href.tex
    :name: url_href-tex
    :linenos:
    
    \documentclass[a4paper,12pt]{article}
    \usepackage[utf8]{inputenc}
    \usepackage[spanish]{babel}
    \usepackage{hyperref}
    \begin{document}
    El link completo de la documentación del paquete hyperref es \url{https://ctan.dcc.uchile.cl/macros/latex/contrib/hyperref/doc/hyperref-doc.pdf}
    
    Aunque notemos que el enlace es muy largo, por lo tanto, podemos hipervincular un texto como sigue \href{https://ctan.dcc.uchile.cl/macros/latex/contrib/hyperref/doc/hyperref-doc.pdf}{link de documentación}
    \end{document}

En general podemos agregar opciones

.. code-block:: latex
    :caption: opciones_url_href.tex
    :name: opciones_url_href-tex
    :linenos:
    
    \href[opciones]{URL}{texto}

Las opciones de argumentos opcionales reconocen las opciones de hyperref llamadas ``pdfremotestartview``,  ``pdfnewwindow`` y las siguientes opciones de valor clave:

- ``page``: especifica el número de página de inicio de los documentos PDF remotos. La primera página es la 1.
- ``ismap``: clave booleana, si se establece en verdadero, la URL debe agregar las coordenadas como parámetros de consulta del visor de PDF.
- ``tenextactionraw``: el valor de los diccionarios clave ``/Next`` de acciones, consulte la especificación PDF.

Macro ``hypersetup``
~~~~~~~~~~~~~~~~~~~~~
La configuración estándar debería estar bien para la mayoría de los usuarios, pero si desea cambiar algo, también es posible. Hay varias variables y dos métodos para pasarlas al paquete. Las opciones se pueden pasar como un argumento del paquete cuando se carga (la forma estándar en que funcionan los paquetes), o el comando ``\hypersetup`` se puede usar de la siguiente manera. 

Luego de introducir el comando ``\usepackage{hyperref}`` se introduce 

.. code-block:: latex
    :caption: hypersetup.tex
    :name: hypersetup-tex
    :linenos:

    \hypersetup{opcion = valor}

Por ejemplo,

.. code-block:: latex
    :caption: ejemplo_hypersetup.tex
    :name: ejemplo_hypersetup-tex
    :linenos:
    
    \documentclass[a4paper,12pt]{book}
    \usepackage[utf8]{inputenc}
    \usepackage[spanish]{babel}
    \usepackage{hyperref}
    \hypersetup{
        pdftitle={Paquete Hyperref},
        pdfauthor={Author},     
        pdffitwindow=true,         
        colorlinks=true,
        linkcolor=blue,
        filecolor=magenta,      
        urlcolor=cyan,
    }

Conflicto con Section
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

El paquete ``hyperref`` toma el texto de los marcadores a partir de los argumentos de comandos como ``\section``, que pueden contener elementos como matemáticas, colores o cambios de fuente, ninguno de los cuales se mostrará en los marcadores tal cual. El comando macro funciona dentro del texto 

.. code-block:: latex
    :caption: texorpdfstring.tex
    :name: texorpdfstring-tex
    :linenos:
    
    \texorpdfstring{TEXstring}{PDFstring}

Por ejemplo,

.. code-block:: latex
    :caption: texorpdfstring.tex
    :name: ejemplo_texorpdfstring-tex
    :linenos:
    
    \section{Pitágoras:
        \texorpdfstring{$ a^2 + b^2 = c^2 $}{%
        a\texttwosuperior\ + b\texttwosuperior\ =
        c\texttwosuperior
        }%
    }
    \section{\texorpdfstring{\textcolor{red}}{}{Red} Mars}
    
``\pdfstringdef`` ejecuta el gancho antes de expandir la cadena. Por lo tanto, puede utilizar este enlace para realizar tareas adicionales o para deshabilitar comandos adicionales.

Enlaces.
---------------------------------------------------------

Notas al pie y notas al margen.
---------------------------------------------------------