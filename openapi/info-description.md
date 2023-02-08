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
