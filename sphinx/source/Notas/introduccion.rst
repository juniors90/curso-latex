Introducción a :math:`\LaTeX{}`
================================

Documentación :math:`\LaTeX{}`.
--------------------------------------------------

Estimados estudiantes, la primera pregunta que nos surge cuando queremos componer documentos científicos de alta calidad es ¿qué herramientas debería utilizar?. Entonces, investigando llegamos a que la mejor opción es :math:`\LaTeX{}`, pero... ¿Qué es :math:`\LaTeX{}`?.

:math:`\LaTeX{}` es software libre bajo licencia LPPL, especializado en la composición de textos cientificos, que consiste en un gran conjunto de macros de :math:`\TeX{}`. Fue escrito por `Leslie Lamport <https://es.wikipedia.org/wiki/Leslie_Lamport>`_, en *1984* , con la intención de facilitar el uso del **lenguaje de composición tipográfica**, :math:`\TeX{}` creado por `Donald Knuth <https://es.wikipedia.org/wiki/Donald_Knuth>`_.

Introducción al Lenguaje :math:`\TeX{}`.
--------------------------------------------------

Este lenguaje (:math:`\TeX{}`) crea diversos archivos de respaldo, entre ellos un archivo de extensión ".dvi" con las instrucciones de cómo se debe imprimir. En la actualidad se utiliza :math:`\text{pdf}\LaTeX{}` para pasar de instrucciones :math:`\LaTeX{}` a un ".pdf".

Notamos que :math:`\LaTeX{}` presupone un cambio de profundo en la manera de pensar para el que está habituado a escribir textos utilizando procesadores de textos comerciales, ya que emplea una filosofía de trabajo diferente a la de los procesadores de texto habituales (conocidos como **WYSIWYG**, es decir, "lo que ves es lo que obtienes") y se basa en instrucciones.

Tradicionalmente, este aspecto se ha considerado una desventaja (probablemente la única). En este **seminario-taller**, apuntamos a describir los fundamentos básicos para la elaboración de textos en :math:`\LaTeX{}`, dando a conocer el entorno de desarrollo, los comandos principales para la codificación de un artículo, la implicancia de la utilización del sistema (integrar el núcleo con nuestro editor de textos preferido) y la calidad tipográfica resultante.

CTAN.
--------------------------------------------------

`CTAN <https://www.ctan.org/>`_ es la abreviación de **"Comprehensive TEX Archive Network (CTAN)"**, que es el lugar central para encontar documentación de todos materiales referentes a :math:`\TeX{}`. CTAN posee actualmente *5990* paquetes disponibles para los usuarios y cerca de *2757* contribuyentes que mantiene activa la documentación. La mayoría de los paquetes son libres y pueden ser descargados y utilizados al instante.

Instalación.
--------------------------------------------------

Documento ".tex".
--------------------------------------------------

Habitualmente, usamos sofwares para procesar textos, éstos que tienen integradas la escritura la composición, la visualizción y la impresión del documento final. En este sistema de construcción de textos académicos de alta calidad, estas tareas son realizadas por diversos componentes, que detallaremos a continuación:

1. **Escritura**: Un documento en :math:`\LaTeX{}` es creado con una extensión ".tex" y se recomienda que sea guardado luego ser compilado. Es un tipo que documento que para su escritura utiliza los caracteres ASCII (`American Standard Code for Information Interchange <https://es.wikipedia.org/wiki/ASCII>`_).
    
   .. include:: ascii.tex

   Esto quiere decir que cualquier editor que contenga estos standares de codificación podran servir para editar nuestro archivo, que luego guardaremos con extensión ".tex".

2. **Compilación**: una vez que se compila el docmento se obtiene una fichero con la extensión ".dvi" pero con el mismo nombre. Este es importante pues es el cual nos permite visualizar nuetro documento. Luego del proceso de compilación, el procesador crea varios archivos con extnsiones ".aux", ".dvi", ".log", ".pdf", ".ps", "etc".
    
    .. code-block:: none

        mi-proyecto/
        |_ img/
        |_ mi_documento.aux
        |_ mi_documento.log
        ...
        |_ mi_documento.pdf
        |_ mi_documento.tex
        |_ mi_documento.toc

Estructura General de un documento.
--------------------------------------------------

Clase de documento/documentclass
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

La clase de documento es el encargado de indicar a :math:`\LaTeX{}` el tipo de documento e información opcional, que :math:`\LaTeX{}` necesitará para formatear nuestro documento correctamente.

Las `clases de documentos <https://ctan.org/topic/class>`_ incluyen `article <https://ctan.org/pkg/article>`_, `book <https://ctan.org/pkg/book>`_, `letter <https://ctan.org/pkg/letter>`_, `report <https://ctan.org/pkg/report>`_, `beamer <https://ctan.org/pkg/beamer>`_, `leafleft <https://ctan.org/pkg/leaflet>`_, etc.

Preámbulo.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

El preámbulo es la primera sección de entrada del archivo. Se declara antes del cuerpo del documento en sí. El preámbulo se usa por completo en todo documento :math:`\LaTeX{}`, es decir, no existe un documento "elaborado" que no posea un preámbulo.

El lenguaje :math:`\LaTeX{}` consta de un "preámbulo" seguido de "texto del documento".

.. code-block:: latex
    :caption: preambulo.tex
    :name: prembulo-tex
    :linenos:

    \documentclass[a4paper, 11pt]{article}
    % nuestro preámbulo va aquí
    \begin{document}
        % texto del documento
    \end{document}


El preámbulo incluye definiciones del titulo, autor, fecha, el uso de paquetes, definición de nuevos comandos y redefinición de comandos que :math:`\LaTeX{}` trae por defecto. Todo esto lo veremos en un ejemplo de la siguinte sección.

Uso de Paquetes.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:math:`\LaTeX{}` proporciona muchas funciones por defecto, pero en algunas situaciones puede resultar útil utilizar lo que llamamos "paquetes". Estos se deben importar, simplemente agregando la directiva ``\usepackage`` al preámbulo  de nuestro documento, por ejemplo:

.. code-block:: latex
    :caption: paquetes.tex
    :name: paquetes-tex
    :linenos:

    \documentclass[a4paper, 11pt]{article}
    \usepackage[utf8]{inputenc}
    \usepackage[spanish]{babel}
    \usepackage[t1]{fontenc}
    % más paquetes, los que necesitemos XD...
    \title{Seminario-Taller: Introducción a la Escritura en \LaTeX{}}
    \author{Ferreira, Juan David}
    \date{\today}
    \begin{document}
        % texto del documento
    \end{document}

Instalar un paquete
+++++++++++++++++++++++++++++++

Al usar Linux o Mac, la mayoría de los paquetes ya estarán instalados de forma predeterminada y, por lo general, no es necesario instalarlos. En caso de que Ubuntu instale  texlive-full desde el administrador de paquetes, se proporcionarían todos los paquetes disponibles. El paquete MiKTeX en Windows descargará el paquete si lo incluye en su documento.

Propósito de los paquetes
+++++++++++++++++++++++++++++++

Existen infinidad de paquetes, todos para diferentes propósitos y en este curso introductorio a la escritura academica en :math:`\LaTeX{}` solo explicaremos los más útiles para iniciarnos en el lenguaje. Para componer matemáticas, :math:`\LaTeX{}` ofrece (entre otros) un entorno de ecuación. Todo dentro de este entorno se imprimirá en modo matemático, que es un entorno de composición tipográfica especial para matemáticas. todo esto lo veremos en una sección especial, dedicada al "Modo matemático". 

.. :math:`\LaTeX{}` también se encarga de los números de ecuación por nosotros.

El cuerpo del documento.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~