Imágenes y figuras
===================

El objetivo principal de este encuentro es la introducción de **Figuras** y **Tablas** dentro de nuestro documento :math:`\LaTeX{}`. El paquete ``graphicx``, nos permite compilar figuras en cualquier formato utilizando el comando ``\includegraphics[options]{my_image}``. Para el manejo de imágenes como fotografías, capturas de pantallas, etc., podemos usar los formatos ``.JPG`` y ``.PNG``. Uno de los formatos aceptados es el formato con extensión ``.eps`` (*Encapsuled PostScripts*).

Introducción a los paquetes de imagenes y figuras.
---------------------------------------------------

+------------+---------------------+--------------------------------------------------------+
| Opciones   | tipo                | Descripción                                            |
+============+=====================+========================================================+
| scale      | numérico            | Es un factor de escalamiento                           |
+------------+---------------------+--------------------------------------------------------+
| width      | longitud            | Es el ancho al que se debe escalar la figura           |
+------------+---------------------+--------------------------------------------------------+
| height     | longitud            | Es el alto al que se debe escalar la figura .          |
+------------+---------------------+--------------------------------------------------------+
| clip       | true/false          | Excluye todo lo que esté fuera del cuadro delimitador. |
+------------+---------------------+--------------------------------------------------------+
| trim       | dllx dlly durx dury | Reduce el cuadro delimitador en la cantidad            |  
|            |                     | especificada.                                          |
+------------+---------------------+--------------------------------------------------------+

Para utilizar la opción ``trim``, debemos asignar cuatro valores separados por espacios ``trim={<izquierda> <abajo> <derecha> <arriba>}``. Después de configurar estos valores, debemos activar el recorte con ``clip=true`` o simplemente ``clip``.

Insertar imágenes y Figuras en un documento.
---------------------------------------------------

El paquete ``graphicx``, nos permite compilar figuras en cualquier formato utilizando el comando ``\includegraphics[opciones]{imagen}``

.. code-block:: latex
    :caption: graphicx.tex
    :name: graphicx-tex
    :linenos:

    \documentclass[a4paper, 11pt]{article}
    \usepackage[utf8]{inputenc}
    \usepackage[spanish]{babel}
    \usepackage[t1]{fontenc}
    % más paquetes, los que necesitemos XD...
    \usepackage{graphicx}   %% --> nos permite insertar figuras
    \title{Seminario-Taller: Introducción a la Escritura en \LaTeX{}}
    \author{Ferreira, Juan David}
    \date{\today}
    \begin{document}
        % figura en el documento
        \includegraphics[scale=0.5]{my_imagen.png}
    \end{document}

Si deseamos compilar una imagen con formato ``.eps``, primero declaramos en nuestro preámbulo el paquete ``epstopdf``, ``\includegraphics[opciones]{imagen}``

.. code-block:: latex
    :caption: epstopdf.tex
    :name: epstopdf-tex
    :linenos:

    \documentclass[a4paper, 11pt]{article}
    \usepackage[utf8]{inputenc}
    \usepackage[spanish]{babel}
    \usepackage[t1]{fontenc}
    % más paquetes, los que necesitemos XD...
    \usepackage{graphicx}   %% --> nos permite insertar figuras
    \usepackage{epstopdf}   %% --> nos permite insertar figuras con extensión .eps
    \title{Seminario-Taller: Introducción a la Escritura en \LaTeX{}}
    \author{Ferreira, Juan David}
    \date{\today}
    \begin{document}
        % figura en el documento
        \includegraphics[scale=0.5]{my_imagen.png}
        % figura con extensión .eps en el documento
        \includegraphics[scale=0.5]{other_imagen.eps}
    \end{document}

Existen casos en los cuales queremos compilar varias figuras colocando una leyenda a cada una de ellas en el mismo entorno. Esto lo podemos hacer usando el paquete ``subfigure``. El comando que imdica que una figura está dividida en varias subfiguras es:

.. code-block:: latex
    :caption: subfigure.tex
    :name: subfigure-tex
    :linenos:

    \documentclass[a4paper, 11pt]{article}
    \usepackage[utf8]{inputenc}
    \usepackage[spanish]{babel}
    \usepackage[t1]{fontenc}
    % más paquetes, los que necesitemos XD...
    \usepackage{graphicx}   %% --> nos permite insertar figuras
    \usepackage{epstopdf}   %% --> nos permite insertar figuras con extensión .eps
    \usepackage{subfigure}   %% --> nos permite insertar varias figuras con leyendas
    \title{Seminario-Taller: Introducción a la Escritura en \LaTeX{}}
    \author{Ferreira, Juan David}
    \date{\today}
    \begin{document}
        % figura en el documento
        \includegraphics[scale=0.5]{my_imagen.png}
        % figura con extensión .eps en el documento
        \includegraphics[scale=0.5]{other_imagen.eps}
        % subfiguras con diferentes extensiónes
        \begin{figure}[h]
            \subfigure[<name_first_image>]{\includegraphics[options]{first_imagefile.eps}}
            \hfill
            \subfigure[<name_second_image>]{\includegraphics[options]{second_imagefile.png}}
        \end{figure}
    \end{document}

Posicionamiento.
---------------------------------------------------