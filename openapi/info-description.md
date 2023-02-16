# ¿Qué es VTEX IO?
VTEX IO es una plataforma de comercio electrónico que ayuda a las empresas a crear su propio eCommerce y vender sus productos en línea. A través de VTEX podrás diseñar tu comercio digital, gestionar productos, recibir órdenes de compra y realizar cobros.

## Instalación vía NPM
De acuerdo a tu sistema operativo, sigue los pasos respectivos para instalar el CLI de VTEX IO en tu computadora.

| Sistema Operativo | Instalación | 
| ----------------- | ----------- |
| MacOs | 1. Instale **Homebrew** siguiendo las instrucciones del sitio web de **Homebrew** |
| | 2. Instalar Node.js a través de Homebrew ejecutando el siguiente comando en tu terminal: ```brew install node``` | 
| | 3. Luego, instalar Yarn : ```brew install Yarn``` | 
| | 4. Finalmente, instale el VTEX IO CLI : ```yarn global add vtex```|
| Linux | 1. Instalar Node.js ejecutando el siguiente comando: ```sudo apt install nodejs``` |
| | 2. Instale Yarn siguiendo la instalación de Yarn para Linux | 
| | 3. Instale VTEX IO CLI ejecutando el siguiente comando: ```sudo yarn global add vtex``` | 
| Windows | 1. Descargue e instale Node.js |
| | 2. Descarga e instala Yarn | 
| | 3. Usa la terminal de Windows con permisos de administrador |
| | 4. Instale VTEX IO CLI ejecutando el siguiente comando: ```yarn global add vtex``` |


Verifica la instalación usando el comando ```vtex``` te deberá mostrar una lista de comandos de vtex y la versión de vtex instalada como se muestra a continuación:

![](https://developers.vtex.com/_next/image?url=https%3A%2F%2Fcdn.jsdelivr.net%2Fgh%2Fvtexdocs%2Fdev-portal-content%40main%2Fimages%2Fvtex-io-documentation-vtex-io-cli-install-4.png&w=3840&q=75) 

### Solución de Problemas de Instalación
Si al ejecutar ```vtex -v``` aparece la versión es porque fue instalado correctamente, de lo contrario reinicia tu computadora porque podría ser un problema de registro.

# VTEX STOREFRONT

Basado en la plataforma de desarrollo VTEX IO y la tecnología React , VTEX Store Framework es responsable de construir el Storefront, proporcionando componentes nativos de comercio electrónico, todos escritos en **JSON**.
Para comenzar a utilizar VTEX IO, primero se debe configurar el entorno de desarrollo, por lo que se necesita instalar el CLI, loguearse en la cuenta **(cliente)**, crear un espacio de trabajo **(workspace)**, y finalmente acceder a la tienda mediante el espacio de trabajo. 

## Configurar Entorno de Desarrollo 
Para configurar el entorno de desarrollo lo hacemos mediante comandos de vtex, estos comandos nos ayudan a crear nuestro entorno donde podemos desarrollar, en esta tabla encontraras los comandos que debes seguir en el mismo orden:

| Comando | Uso |
| ------- | --- |
| vtex login | Esto abrirá una nueva página en el navegador que nos redirigirá a un inicio de sesión | 
| vtex use + nombre de tu workspace | Una vez que inicies sesión por defecto estarás en el workspace de Máster, ten cuidado!! Lo siguiente es crear tu propio workspace usando este comando Esto creará tu espacio de trabajo donde podrás realizar tus cambios sin afectar master!! |
| vtex whoami | Asegurate de que estás en tu workspace usando este comando. Esto te informará en qué cuenta estás logueado, el correo que estás usando y el nombre de tu workspace donde estás trabajando |
| vtex ls | Para ver qué dependencias, aplicaciones o qué temas están instaladas en el workspace usamos el comando: Desplegará una lista con todas las aplicaciones o temas que tiene tu workspace | 
| vtex browse | Para visualizar tu proyecto usamos este comando. Abrirá una ventana en tu navegador con tu proyecto |
| vtex link | Nos vincula el proyecto con el navegador, y cada que se realiza un cambio, se actualiza automáticamente |
| vtex unlink | Nos desvincula el proyecto del navegador | 
| vtex logout | Para salir de tu inicio de sesión | 




# Workspace

## ¿Qué es un Workspace? 
Un workspace es un espacio de trabajo aislado de otros espacios, por ejemplo como una rama de git. Existen 3 tipos de ambiente en **vtex**:

| Ambiente | Permite | No permite |
| -------- | ------- | ---------- | 
| Development | Vinculaciones & Desarrollos | Promover a máster | 
| Producción  | Instalaciones, Recibir tráfico a nivel de producción y llegar a promover a máster | Vinculaciones para desarrollar apps |
| Máster | Contenido presentado al usuario final & Contenido 100% validado | 

## Comandos de Workspace

| Comando | Descripción | 
| ------- | ----------- | 
| workspace abtest | Crea, finaliza o muestra el estado de una prueba | 
| workspace delete | Elimina uno o varios espacios de trabajo de la cuenta actual | 
| workspace list | Enumera todos los espacios de trabajo de la cuenta actual | 
| workspace promote | Promueve el espacio de trabajo actual para dominar. (Solo funciona para espacios de trabajo de producción) | 
| workspace reset | Limpia todas las configuraciones de un espacio de trabajo y las vuelve a crear | 
| workspace status | Muestra información sobre el espacio de trabajo especificado | 
| workspace use | Crea y cambia a un nuevo espacio de trabajo o simplemente cambia  a uno existente | 

También puedes usar el comando ```vtex workspace``` para visualizar los comandos en tu consola.

[Más información](https://www.youtube.com/watch?v=YYo7Ii9_w3s&list=PLTmvmjdoacBR-Dimz5k_DV8-CyLGYfi9i&index=4)

# Init & Link. 
Iniciar el tema de la tienda & 
vincularlo con la tienda

Para utilizar store framework, hay que instalar store theme. Para iniciar con la instalación del tema:
```vtex init``` Nos regresa una lista de opciones, seleccionamos la primera store, confirmamos y se va a generar una copia de un repositorio remoto, que incluye una versión mínima de una aplicación.

![](https://cdn.jsdelivr.net/gh/vtexdocs/dev-portal-content@main/images/vtex-io-documentation-vtex-io-cli-usage-5.png)

A nivel raíz tenemos el archivo 'manifest.json', dentro de sus propiedades tenemos:

**“vendor”: “cuenta”**
Esta propiedad es el responsable de la aplicación ya sea quien la desarrolló o le está 
dando soporte y su valor es el nombre de la cuenta(tienda)

**“name”**
Es el nombre de la aplicación

**“versión”**
Respeta la nomenclatura de la versión

**“builder”**
Hace referencia a los constructores para traducir los archivos locales y enviarlos al workspace. Un builder es responsable de procesar, validar y reenviar un bloque de código determinado a un tiempo de ejecución o un marco capaz de ejecutarlo.

**"dependencies"**
Las dependencias son una lista de aplicaciones previamente definidas y desarrolladas que sirven para exportar los diferentes bloques que se van a utilizar en el tema. Si deseamos agregar algún componente, se busca en la documentación y se agrega a esta lista de dependencias.

Para vincular aplicaciones debemos utilizar workspaces de tipo dev Antes de correr el proyecto, en el archivo de manifest.json, se deben cambiar el valor de "vendor" con el nombre de la cuenta, "name" es opcional cambiarlo por el que preferimos o dejarlo, y en "versión" cambiarlo a “0.0.1” que es un patch para una aplicación que apenas se va a desarrollar. Después de estos cambios, entrar a la carpeta en donde se ubica la aplicación y ubicarse en el workspace que estamos trabajando y correr el comando:

```vtex link```
Nos vincula el proyecto con el navegador, y cada que se realiza un cambio, se actualiza automáticamente

![](https://cdn.jsdelivr.net/gh/vtexdocs/dev-portal-content@main/images/vtex-io-documentation-vtex-io-cli-usage-6.png)

Para desvincular el proyecto utilizamos el comando: 

```vtex unlink```
Nos desvincula el proyecto del navegador

[Más información](https://www.youtube.com/watch?v=bXjb1ApVDWk&list=PLTmvmjdoacBR-Dimz5k_DV8-CyLGYfi9i&index=5)

## Builder
La implementación de la aplicación debe relacionarse con los constructores declarados en el archivo del manifest.json de la aplicación y vivir dentro de las carpetas nombradas sobre los constructores de la aplicación.

## Tipos de Builder
Esta es una lista de constructores VTEX IO:


| Nombre | Funcionalidad | Beta Abierta |
| ------ | ------------- | ------------ |
| admin | Exporta bloques y rutas al VTEX Admin | No abierta | 
| assets | Maneja los activos utilizados por los bloques de temas de la tienda. Obtiene todas las rutas de activos utilizadas y las sube a la base de datos VTEX IO | No abierta |
| configuration | Le permite asignar código perteneciente a configuraciones de servicio a una aplicación que es independiente de la plataforma. | No abierta |
| dotnet | Interpreta el /dotnetdirectorio, potenciando el desarrollo de servicios backend personalizados | No abierta | 
| graphql | Procesa las API y los esquemas de GraphQL interpretando .graphqllos .gqlarchivos contenidos en el /graphqldirectorio de la aplicación | No abierta |
| services | Obtiene los trabajadores de servicio exportados por las aplicaciones instaladas de la cuenta y los agrupa en un solo archivo, lo que permite que la tienda trabaje con varios trabajadores de servicio simultáneament | No abierta| 
| styles | Exporta configuraciones de CSS para bloques de Store Framework. Al compilar su aplicación, el generador de estilos lee el styles/styles.json y usa un generador de taquiones para producir correctamente el CSS de su tienda | Abierta | 
| store | Interpreta y valida los bloques, las interfaces y las rutas contenidas en el /storedirectorio de la aplicación del tema, potenciando los componentes de la tienda Store Framework y construyendo el escaparate | Abierta |
| messages | Exporta mensajes de cadena localizados, potenciando la internacionalización de VTEX IO . Lee .jsonarchivos asociados con diferentes configuraciones regionales dentro del /messagesdirectorio de la aplicación y los pone a disposición de las aplicaciones front-end para que los usen a través de react-intl | Abierta | 
| node | Interpreta el /nodedirectorio, lo que permite el desarrollo de servicios de back-end personalizados mediante Typescript | No abierta |
| pixel | Procesa el código fuente y la configuración de las Pixel Apps en VTEX IO. Los archivos recogidos por este constructor se encuentran en el /pixeldirectorio de la aplicación | No abierta |
| react | Interpreta el /reactdirectorio, potenciando el desarrollo de componentes de React usando Typescript | Abierta |

## Permisos para los tipos de builders
Cada cuenta y socio de VTEX puede usar libremente VTEX IO para desarrollar componentes de escaparate personalizados, lo que significa que la plataforma funciona como una solución beta abierta cuando se trata de proyectos React.

# OVERVIEW ADMIN 
El Admin permite a los comerciantes gestionar todas sus experiencias de comercio digital en un solo lugar, de forma más sencilla e inteligente.
La barra lateral es el punto de partida para todas las áreas de administración. Vea a continuación los detalles sobre su funcionamiento y posibilidades.

![](https://images.ctfassets.net/alneenqid6w5/68DVYFXEFfShDhVJLoP90E/ab49f60e0a7fccda830f4f7cfccdc32b/paginainicial.en.png)

**HOME** 
- Información General 

**ORDERS**
- En el Administrador de Órdenes podemos ver todo lo relacionado con las compras que ocurren en su sitio web 
Manipular su inventario, el envío, establecer algunos puntos de recogida, localizador de tiendas

**TRANSACTIONS**
- Se establecen todos sus pagos, las ofertas de impuestos y una amplia gama de pagos 

**PRODUCTS**
- Está compuesto por catálogo, precios, promociones
- Aquí es donde creas cada producto, tienes la información de todas las categorías de productos, precios, etc

**ANALYTICS**
- Se puede realizar un seguimiento y analizar los pasos de los clientes hasta la finalización de una orden.

**CUSTOMER**
- Ayuda a la gestión de los datos de sus clientes. Esta aplicación permite al usuario crear, editar y buscar clientes. Es una alternativa a MasterData a la hora de gestionar los documentos de la entidad CL.

**STORE SETUP**
- Ayuda a trabajar con multiples politicas comerciales 
- Diferentes modelos o submodelos de para el diseño del sitio web
- Cambiar la información del front-end editandolo
- Establecer estilos 

**MARKETPLACE**
- Trabajar con vendedores, integraciones con ofertas de texto

**ACCOUNT SETTINGS**
- Crear nuevos usuarios, otorgar derechos de acceso a diferentes tipos de usuario

**INSTALLED APPS**
- Instalar aplicaciones y aplicaciones ya instaladas


# Storefront Apps Admin
Aprovechando la plataforma VTEX IO, la solución VTEX IO Store Framework ofrece las bases necesarias para cualquier estructura de escaparate, proporcionando bloques de tienda React personalizables y de alta calidad para que pueda crear (en el tiempo de comercialización más rápido posible). Experiencias de compra integrales que nunca se vuelven obsoletas.
Sin embargo, considerando algunos escenarios comerciales particulares, es posible que sienta la necesidad de soluciones front-end específicas que aún no están cubiertas por nuestros componentes nativos. En este caso, puede desarrollar sus propias aplicaciones de escaparate con React y VTEX IO

## Instalación de Apps 
En el apartado de Apps Store, verás la lista de aplicaciones disponibles para la cuenta que estas gestionando.

![](https://help.fromdoppler.com/wp-content/uploads/2018/12/vtex-1-1.jpg)

# Site Editor
Site Editor es una interfaz gráfica para administrar el contenido de su escaparate. Le permite crear, editar, publicar y programar cambios en los componentes y el comportamiento de su escaparate.  
Para usar Site Editor, vaya al administrador de su tienda y haga clic en Configuración de la tienda > CMS > Site Editor . Verás las principales herramientas disponibles en la interfaz gráfica.


![](https://images.ctfassets.net/alneenqid6w5/5K3z9KH8VLYFh0iYA4UFDX/216b3664d5d3f8b6d901a0b8cf427906/site-editor-ui-en.png)

| Herramienta | Descripcion |
| ----------- | ----------- |
| Configuración regional vinculante | Seleccione la configuración regional de enlace a la que desea aplicar los cambios de contenido. Por ejemplo, inglés (en-GB), portugués (pt-BR) o español (es-AR) |
| URL | Navega entre las páginas de tu tienda |
| Seleccione un bloque | Seleccione el bloque en el que desea crear o modificar contenido |
| Modo de vista	| Verifique los diferentes modos de visualización para asegurarse de que su contenido se muestre correctamente en dispositivos móviles, tabletas y computadoras de escritorio |
| Avance | Vea una vista previa del contenido de su escaparate en Site Editor |
| Bloques | Agregue y edite bloques (por ejemplo, Banner, Menú o Pie de página) para crear y personalizar su escaparate |


# Checkout UI
La aplicación personalizada de la interfaz de usuario de Checkout es responsable de personalizar la interfaz de usuario de Checkout de su tienda a través de la interfaz del administrador.

## Caracteristicas

	- Cambiar exhibición de métodos de pago
	- Fecha de envío simplificada
	- Mostrar el precio unitario del artículo
	- Mostrar campo 'notas'
	- Cambiar estilos de texto
	- Cambiar estilos de bloques
	- Cambiar colores
	- Área CSS avanzada
	- Área avanzada de Javascript
	- Seguimiento de cambios
![](https://extensions.vtexassets.com/arquivos/ids/156909/image-c6e0152bdb674530bbe1bce749692f0a.jpg?v=637456364396300000)
![](https://extensions.vtexassets.com/arquivos/ids/156910/image-3309f98fd23b426682df3c631d2f9426.jpg?v=637456364082130000)
![](https://extensions.vtexassets.com/arquivos/ids/156911/image-515d02f438fd4935a460db7e66b072a5.jpg?v=637456364153070000)


# Páginas que compone una tienda
## Home Page
El home page es la portada de tu tienda web, aquí es donde encontrarás la página de inicio que se muestra en un navegador web cuando se abre la aplicación por primera vez.

### Header
	El header hace referencia a la parte superior del sitio web, los usuarios puedan
	navegar fácilmente por él.

### Footer
	Es la parte inferior de una página web, en la que se incluye una serie de elementos
	que pueden resultar de interés para el usuario que navega por ella, como enlaces a
	las categorías principales, información de contacto, redes sociales o enlaces a textos
	legales.

## PLP  (Product Listing Page) 
En ecommerce es la página destinada a listar una serie de productos que responden a un mismo criterio de búsqueda o clasificación, siendo esa la definición de sus siglas: 
Página de Listado de Producto.

![](https://blog.crobox.com/hubfs/Blog%20Post%20Photos/Product%20listing%20page%20design.jpg)


## PDP (Product Detail Page)
En la estructura de un ecommerce, PDP es la página de descripción de producto o lo que es lo mismo, la ficha del propio producto.

![](https://blog.crobox.com/hubfs/Blog%20Post%20Photos/2015%20Blog%20Content/PDP%20best%20practices.jpg)


## Checkout
El checkout en ecommerce es la parte final del proceso de compra, cuando el cliente confirma el carrito con los productos o servicios seleccionados, introduce sus datos y completa el pago. 

![](https://thumbor.forbes.com/thumbor/fit-in/x/https://www.forbes.com/advisor/wp-content/uploads/2022/09/monki.png)


# REACT + PROPS CÓMO CREAR BLOQUES PERSONALIZADOS EN VTEX IO
Blocks Props, identificadores, blocks

Los blocks son los json desarrollados por VTEX, y son una abstracción de un componente React. Deben estar declarados en las dependencias del manifest.json y editar su contenido en donde se estén utilizando dichos bloques. 
Para personalizar un componente, en los bloques se hace mediante la propiedad “props”, se debe leer la documentación de VTEX IO, y ubicar los bloques para ver qué propiedades se pueden utilizar en cada bloque.
Es una buena práctica que cada bloque tenga su identificador, de la siguiente manera:

# Templates

Los Templates son archivos que contienen el código de las páginas de tu sitio web. Son responsables, entre otras cosas, de determinar cómo aparecerá la información en la pantalla. La estructura de las secciones de la tienda se deben mediante templates, que a su vez mandan a llamar los blocks correspondientes a cada módulo requerido para las diferentes funcionalidades de cada página.
