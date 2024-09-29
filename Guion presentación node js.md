<b>¿Qué es Node.js?</b>

Node.js es un entorno de ejecución de JavaScript basado en el motor V8 de Google, 
que es el mismo motor que utiliza Google Chrome para ejecutar JavaScript en el 
navegador. Node.js permite ejecutar JavaScript en el lado del servidor, fuera del 
navegador, lo que lo convierte en una herramienta poderosa para construir 
aplicaciones web escalables y eficientes.

A diferencia de los servidores tradicionales que crean un nuevo hilo para cada 
solicitud, Node.js ejecuta todas las solicitudes en un solo proceso utilizando un 
modelo de concurrencia basado en eventos. Este modelo no bloqueante (non-
blocking) permite a Node.js manejar múltiples conexiones simultáneamente sin crear 
nuevos hilos para cada una. En lugar de detenerse y esperar una respuesta, Node.js 
continúa ejecutando otras tareas y gestiona las respuestas cuando están disponibles, 
lo que mejora la eficiencia y la escalabilidad.

Además, una de las grandes ventajas de Node.js es que permite a los desarrolladores 
utilizar el mismo lenguaje, JavaScript, tanto en el front-end como en el back-end, lo 
que facilita la coherencia en el desarrollo de aplicaciones web.

<b>Node.js y el navegador</b>

Aunque tanto en el desarrollo frontend como en Node.js se utiliza el lenguaje de 
programación JavaScript, existen diferencias importantes entre ambos entornos. En 
el frontend, JavaScript interactúa con el DOM (Document Object Model) y tiene 
acceso a objetos específicos del navegador, como document y window. En Node.js, 
no se interactúa con el DOM ni se dispone de estos objetos, ya que Node.js se 
ejecuta en un entorno de servidor, donde esos elementos no son necesarios ni están 
disponibles.

Una ventaja de Node.js es que permite controlar la versión que se utiliza en tu 
proyecto. Esto significa que puedes escribir tu código utilizando las últimas 
características del estándar ECMAScript (ES2015+), siempre y cuando estén 
soportadas por la versión de Node.js que estás utilizando.

Otra diferencia clave es que Node.js soporta dos sistemas de módulos: CommonJS 
(el sistema de módulos original de Node.js) y ES Modules (un sistema más reciente 
que sigue el estándar ECMAScript). Esta flexibilidad en el manejo de módulos es una 
característica importante de Node.js.


<b>npm</b>

Npm (Node Package Manager) comenzó como una herramienta para descargar y gestionar dependencias en proyectos de Node.js, pero su crecimiento ha sido tan significativo que, en 2022, se reportó que tenía más de 2.1 millones de paquetes disponibles. Esta vasta colección de paquetes lo convierte en una pieza clave en el ecosistema de desarrollo JavaScript.

Para instalar todas las dependencias de un proyecto, simplemente puedes correr el comando

npm install ó npm i

Este comando lee el archivo package.json del proyecto y descarga todas las dependencias especificadas.

Instalación de paquetes específicos

Si necesitas instalar un paquete específico y agregarlo a las dependencias de tu proyecto, puedes usar:

npm install nombre-paquete

Este comando añade automáticamente el paquete al archivo package.json en la sección de dependencias. Si quieres añadir el paquete a las dependencias de desarrollo, puedes usar:

npm install nombre-paquete --save-dev

Para dependencias opcionales:

npm install nombre-paquete --save-optional

Actualización de paquetes y manejo de versiones

Npm también permite actualizar paquetes y manejar versiones específicas. Para actualizar un paquete a su última versión compatible, puedes usar:

npm update nombre-paquete

Si deseas instalar una versión específica de un paquete, puedes hacerlo así:

npm install nombre-paquete@1.2.3

Ejecución de scripts

El archivo package.json no solo contiene las dependencias, sino que también permite definir scripts que se pueden ejecutar con npm. Estos scripts se definen en una sección llamada "scripts", y puedes correrlos con:

npm run nombre-script


<b>Package.json</b>

El package.json es un archivo en formato JSON que se encuentra en la raíz de un proyecto de Node.js. Este archivo contiene metadatos sobre el proyecto, como su nombre, versión, autor, y una lista de scripts y dependencias que el proyecto utiliza. Es fundamental para garantizar la replicabilidad y gestión del proyecto, permitiendo a otros desarrolladores y sistemas automatizados entender cómo configurar y ejecutar el proyecto.

Estructura del package.json

El archivo package.json se compone de varios campos clave, algunos de los cuales son opcionales. Aquí están los más comunes:

name: El nombre del proyecto o paquete. Debe ser único si se publica en un registro público como npm.

version: La versión actual del proyecto, siguiendo el esquema de versionado semántico (SemVer), por ejemplo, "1.0.0".

description: Una breve descripción del proyecto, que explica su propósito o funcionalidad.

main: El punto de entrada principal del proyecto, que especifica el archivo que se ejecutará cuando alguien requiera el paquete. Comúnmente es "index.js".

scripts: Una sección donde se definen comandos de scripts personalizados que se pueden ejecutar con npm run script-name. Estos scripts se utilizan para automatizar tareas como pruebas, compilación, o despliegue. Ejemplos:

dependencies: Una lista de dependencias que el proyecto necesita para funcionar en producción. Cada dependencia se especifica con su nombre y versión. Ejemplo:

devDependencies: Similar a dependencies, pero estas son dependencias necesarias solo durante el desarrollo del proyecto, como herramientas de prueba o transpiladores. Ejemplo:

optionalDependencies: Dependencias opcionales que no son críticas para el proyecto, pero que se pueden instalar si están disponibles.

peerDependencies: Especifica las versiones de los paquetes que son compatibles con tu proyecto, pero que no se instalan automáticamente. Esto es útil cuando estás desarrollando bibliotecas que dependen de otras bibliotecas.

engines: Define las versiones de Node.js y npm que son compatibles con tu proyecto, lo que ayuda a asegurar que el proyecto se ejecute en un entorno compatible. Ejemplo:

license: Especifica la licencia bajo la cual se distribuye el proyecto, como "MIT" o "ISC".

author y contributors: Información sobre el autor principal y otros contribuidores al proyecto.

¿Por qué es importante el package.json?

El package.json no solo facilita la instalación y gestión de las dependencias, sino que también estandariza la forma en que se configuran y ejecutan los proyectos Node.js. Es crucial para asegurar que cualquier persona que clone o descargue tu proyecto pueda configurarlo y ejecutarlo sin problemas, simplemente usando comandos como npm install o npm run.

Además, es el punto de referencia para muchos servicios de integración continua (CI/CD), como Travis CI o Jenkins, que lo utilizan para automatizar la construcción, prueba, y despliegue de proyectos.


<b>Módulos</b>

Los módulos en Node.js son bloques de código encapsulados que poseen su propio alcance y funcionalidad. Estos permiten estructurar el proyecto de manera modular, lo cual facilita la reutilización de código. 

Node.js incluye módulos integrados por defecto, pero también es posible utilizar módulos de terceros o crear módulos personalizados. 

Para utilizar un módulo, es necesario importarlo, y existen dos enfoques para hacerlo: CommonJS y ECMAScript Modules (ESM). 

En CommonJS, se emplea la sintaxis

const { modulo1, modulo2, ... } = require('ruta-modulo');, 

mientras que en ESM se utiliza

import { modulo1, modulo2, ... } from 'ruta-modulo';.

y se le debe colocar la extensión .mjs al archivo 