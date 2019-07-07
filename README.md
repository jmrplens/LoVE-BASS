<p align="center">
<img src="https://jmrplens.com/GitHub_LoVEBASS/logo-square.png" width="20%"></img>

<h3 align="center"><b> Loudspeakers for Vented Enclosures: a Backwards Approach for Speaker Selection </b></h3>
<h3 align="center"><b> V0.9 (June 2019) </b></h3>
</p>

- Software bajo pruebas y verificación.
- Requiere MATLAB R2018 o posterior. 
- Compatible con Windows y Mac OS.

#### Instaladores (No requiere MATLAB)

<table>
    <thead>
        <tr>
            <th>OS</th>
            <th>Installers</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td rowspan=2>Mac OS</td>
            <td><a href="https://jmrplens.com/GitHub_LoVEBASS/installers-0.9/LoVE-BASS_v0.9_ONLINE_MacOS.zip">Online (requires internet connection)</a></td>
        </tr>
        <tr>
            <td><a href="https://jmrplens.com/GitHub_LoVEBASS/installers-0.9/LoVE-BASS_v0.9_OFFLINE_MacOS.zip">Standalone</a></td>
        </tr>
        <tr>
            <td rowspan=2>Windows</td>
            <td><a href="https://jmrplens.com/GitHub_LoVEBASS/installers-0.9/LoVE-BASS_v0.9_ONLINE_Windows.zip">Online (requires internet connection)</a></td>
        </tr>
        <tr>
            <td><a href="https://jmrplens.com/GitHub_LoVEBASS/installers-0.9/LoVE-BASS_v0.9_OFFLINE_Windows.zip">Standalone</a></td>
        </tr>
    </tbody>
</table>

## Índice
<!-- MarkdownTOC -->

- [Información general](#informaci%C3%B3n-general)
	- [Parámetros + Base de datos](#par%C3%A1metros--base-de-datos)
	- [Altavoz personalizado](#altavoz-personalizado)
- [Research \(hidden options\)](#research-hidden-options)
	- [Alineamiento + Base de datos \(QB3|SC4\)](#alineamiento--base-de-datos-qb3%7Csc4)
- [En desarrollo](#en-desarrollo)
- [Desarrolladores](#desarrolladores)

<!-- /MarkdownTOC -->


<a id="informaci%C3%B3n-general"></a>
### Información general
Aplicación para el diseño inverso de cajas abiertas (bass reflex) utilizando base de datos o alineamiento.
La aplicación, desarrolada con App Designer de MATLAB®, dispone de varias opciones explicadas a continuación.

---
<a id="par%C3%A1metros--base-de-datos"></a>
#### Parámetros + Base de datos
<img src="https://jmrplens.com/GitHub_LoVEBASS/parametros.png" width="20%"></img>

En este caso se analiza uno a uno cada altavoz de la base de datos y se modifican sus parámetros utilizando un cálculo iterativo (potencia, volumen de la caja, frecuencia de corte a -3dB, dimensiones del puerto) para encontrar los altavoces que mejor se ajustan a los parámetros buscados.

Un ejemplo de los resultados se muestra a continuación:

<img src="https://jmrplens.com/GitHub_LoVEBASS/resulparametrosn.png" width="45%"></img>

Como se puede observar se ofrecen 4 altavoces que ofrecen las respuestas más aproximadas a lo buscado pero fijando alguno de los parametros (máximo SPL, mínimo f3, minimo volumen de la caja, mínimo tamaño del puerto). Además se puede afinar aun más el resultados modificando la frecuencia de la caja, el volumen de la caja y el SPL máximo y observando gráficamente el resultado.

Es posible seleccionar múltiples altavoces de la tabla para representarlos conjuntamente y compararlos:

<img src="https://jmrplens.com/GitHub_LoVEBASS/plotconjunton.png" width="45%"></img>

En la opción `File->Export result list` se puede exportar la tabla completa de resultados en formato texto, Excel o M-file.

<a id="altavoz-personalizado"></a>
#### Altavoz personalizado
<img src="https://jmrplens.com/GitHub_LoVEBASS/custom.png" width="20%"></img>

En este caso se calculan los parámetros de un altavoz hipotético o que se prevee fabricar con los parámetros iniciales (imagen superior). Si en algún caso se excede de las posibilidades físicas de un altavoz se mostrará una o varias advertencias indicando los problemas del diseño elegido.
Las representaciones y los datos mostrados se calculan cada vez que se modifica algún parámetro.

<img src="https://jmrplens.com/GitHub_LoVEBASS/resulcustomn.png" width="45%"></img>

---
<a id="research-hidden-options"></a>
### Research (hidden options)
La aplicación contiene y contendrá funciones extra que no estarán activadas por defecto, para ello hay que acceder el código y modificar la variable `research` al inicio de la función `startupFcn`:

```Matlab
function startupFcn(app)
            %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
            % Extra functions (research purpose): change to 'true'
            app.research = false;
            %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
```


A continuación se describen la opciones que se habilitan al activar el modo _research_

<a id="alineamiento--base-de-datos-qb3%7Csc4"></a>
#### Alineamiento + Base de datos (QB3|SC4)
<img src="https://jmrplens.com/GitHub_LoVEBASS/alineamiento.png" width="40%"></img>

A través de unos parámetros buscados para el conjunto final de caja+altavoz se calculan los parametros de todos los altavoces contenidos en la base de datos (es editable y ampliable fácilmente) y se muestran todos los modelos válidos que pueden ofrecer esos parámetros buscados al inicio. Todos los modelos se pueden analizar, tanto todos los parámetros electroacústicos como sus curvas de SPL y desplazamiento del cono.
Se incluye el cálculo de las dimensiones del puerto y la potencia a aplicar al altavoz entre otros parámetros, un resultado típico sería el siguiente:

<img src="https://jmrplens.com/GitHub_LoVEBASS/resulalineamienton.png" width="45%"></img>   <img src="https://jmrplens.com/GitHub_LoVEBASS/resulalineamiento2n.png" width="45%"></img>

Es posible seleccionar múltiples altavoces de la tabla para representarlos conjuntamente y compararlos:

<img src="https://jmrplens.com/GitHub_LoVEBASS/plotconjunton.png" width="45%"></img>

En la opción `File->Export result list` se puede exportar la tabla completa de resultados en formato texto, Excel o M-file.

---
<a id="en-desarrollo"></a>
### En desarrollo
Algunas funciones que aparecen en el menú principal aun no están disponibles:
* Español
* Guardar y cargar la sesión
* Ventanas de ayuda para cada uno de los métodos de diseño

Tambien está previsto actualizar y ampliar la base de datos.

---
<a id="desarrolladores"></a>
### Desarrolladores
* Jose Manuel Requena Plens (info@jmrplens.com ; https://jmrplens.com)
* Francisco Sales Castells Ramón (fcastells@eln.upv.es ; http://www.upv.es/ficha-personal/fracasra)
