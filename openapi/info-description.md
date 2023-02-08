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

Basado en la plataforma de desarrollo VTEX IO y la tecnología React , VTEX Store Framework es responsable de construir el Storefront, proporcionando componentes nativos de comercio electrónico, todos escritos en JSON.
Para comenzar a utilizar VTEX IO, primero se debe configurar el entorno de desarrollo, por lo que se necesita instalar el CLI, loguearse en la cuenta (cliente), crear un espacio de trabajo (workspace), y finalmente acceder a la tienda mediante el espacio de trabajo. 

# Comandos Básicos

| Comando | Uso |
| ------- | --- |
| vtex login | Esto abrirá una nueva página en el navegador que nos redirigirá a un inicio de sesión | 
| vtex logout | Para salir de tu inicio de sesión | 
| vtex use + nombre de tu workspace | Una vez que inicies sesión por defecto estarás en el workspace de Máster, ten cuidado!! Lo siguiente es crear tu propio workspace usando este comando Esto creará tu espacio de trabajo donde podrás realizar tus cambios sin afectar master!! |
| vtex whoami | Asegurate de que estás en tu workspace usando este comando. Esto te informará en qué cuenta estás logueado, el correo que estás usando y el nombre de tu workspace donde estás trabajando |
| vtex ls | Para ver qué dependencias, aplicaciones o qué temas están instaladas en el workspace usamos el comando: Desplegará una lista con todas las aplicaciones o temas que tiene tu workspace | 
| vtex browse | Para visualizar tu proyecto usamos este comando. Abrirá una ventana en tu navegador con tu proyecto |

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

**“vendor”: “vtex”**
Esta propiedad es el responsable de la aplicación ya sea quien la desarrolló o le está 
dando soporte y su valor es el nombre de la cuenta(tienda)

**“name”**
Es el nombre de la aplicación

**“versión”**
Respeta la nomenclatura de la versión

**“builder”**
Hace referencia a los constructores para traducir los archivos locales y enviarlos al workspace

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
