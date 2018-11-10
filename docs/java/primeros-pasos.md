# Índice

1. [Introducción](#introducción) - Breve explicación sobre JDA.
2. [Instalación](#instalación) - Coḿo instalar y/o usar JDA en nuestro sistema.
    * [Requisitos](#requisitos) - Software necesario para la instalación de JDA.
    * [Maven](#versión-maven) - Instalación con el sistema de versionado Maven.
        - [NetBeans](###netbeans-maven) - Instalación para el IDE NetBeans.
        - [Eclipse](###eclipse-maven) - Instalación para el IDE Eclipse Oxygen.
        - [IntelliJ](###intellij-idea-maven) - Instalación para el IDE IntelliJ IDEA.
    * [JAR](#versión-jar) - Instalación con el sistema de librerías JAR.
        - [NetBeans](###netbeans-jar) - Instalación para el IDE NetBeans.
        - [Eclipse](###eclipse-jar) - Instalación para el IDE Eclipse Oxygen.
        - [IntelliJ](###intellij-idea-jar) - Instalación para el IDE IntelliJ IDEA.
3. [Requisitos Obligatorios](#dependencias) - Software necesario para el correcto uso de JDA.
4. [Ejemplos de Uso](#ejemplos-de-uso) - Serie de ejemplos sobre el uso de JDA.
    - [Instanciado el Bot](###ejemplo-1-instanciando-el-bot) - Creando el objeto que será nuestro Bot.
    - [Capturar Mensajes](###ejemplo-2-capturando-mensajes) - Leyendo y capturando el contenido de un mensaje.
    - [Enviar Mensajes](###ejemplo-3-enviar-mensajes) - Respondiendo un mensaje.

# Introducción

[JDA](https://github.com/DV8FromTheWorld/JDA "JDA GitHub") *(Java Discord API)* es un API Wrapper para [Discord API](https://discordapp.com/developers/docs/intro "Discord API Documentation") que facilita enormemente su uso, es decir, una herramienta para hacer más accesible la API de Discord.

**JDA** fue desarrollado por [Austin Keener](https://github.com/DV8FromTheWorld/ "Developer Home") sirviendo como librería para la creación, manejo y modificación de Bots en Java.

# Instalación

[![JDK](https://img.shields.io/badge/JDK-8+-red.svg)](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html "JDK 8 Download")
[![Maven](https://img.shields.io/badge/Maven-Lastest-yellow.svg)](https://maven.apache.org/ "Maven Download")
[![JDA Version](https://img.shields.io/badge/JDA-Lastest-lightgrey.svg)](https://github.com/DV8FromTheWorld/JDA "JDA GitHub")
[![JDA Wiki](https://img.shields.io/badge/JDA-Wiki-blue.svg)](https://github.com/DV8FromTheWorld/JDA/wiki "JDA Wiki")

- [Requisitos](###requisitos)
- [Instalación con Maven](###versión-maven)
- [Instalación con JAR](###versión-jar)

---

### Requisitos

Para hacer uso de la librería **JDA** necesitaremos tener [JDK 8](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html "JDK 8 Download") o superior instalado en nuestro Sistema.

Podemos comprobar si tenemos **JDK 8** instalando escribiendo `java -version` en la consola de nuestro Sistema Operativo.

Aunque se puede compilar y ejecutar por consola, en esta explicación usaremos un IDE (Entorno de Desarrollo) para facilitarnos el proceso de usar librerías externas, y se explicará tanto el uso directo de dependencias (archivo JAR), como el uso de proyectos Maven.

Se hará un explicación para los IDEs: *NetBeans*, *Eclipse* e *IntelliJ IDEA*.

#### Links de Descarga

- [JDK 8 (Java Development Kit)](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html "JDK 8 Download")
- [Archivos JAR de JDA](https://github.com/DV8FromTheWorld/JDA/releases/ "Archivos JAR")
- [NetBeans IDE](https://netbeans.org/ "NetBeans Homepage")
- [Eclipse](https://www.eclipse.org/ide/ "Eclipse Homepage")
- [IntelliJ IDEA](https://www.jetbrains.com/idea/ "IntelliJ IDEA Homepage")

---

### Versión Maven

El sistema de versiones y dependencias de Maven nos permite usar librerías externas sin necesidad de descargar el JAR de estas, con la simple modificación del archivo `pom.xml` propio de los proyectos Maven.

Partiendo de que un documento `pom.xml` base sería así:

```xml
<!--Etiqueta project, groupId, name y otras cosas-->
<properties>
    <!--Más etiquetas con propiedades-->
</properties>

<!--Aquí debería estar la etiqueta <dependencies>, si no está simplemente la creamos.-->
<dependencies>
    <!--Si ya existía previamente la etiqueta, simplemente añadimos las <dependency>-->
    <!--Añadimos el JDA-->
    <dependency>
        <groupId>net.dv8tion</groupId>
        <artifactId>JDA</artifactId>
        <!--Deberemos poner la versión correspondiente del JDA que estemos usando-->
        <version>VERSION</version>
    </dependency>
</dependencies>

<!--De igual manera que con <dependencies>, si no está <repositories>, se crea-->
<repositories>
    <!--Añadimos lo siguiente-->
    <repository>
        <id>jcenter</id>
        <name>jcenter-bintray</name>
        <url>http://jcenter.bintray.com</url>
    </repository>
</repositories>
```

Lo siguiente será crear los proyectos Maven según el IDE que vayamos a usar.

- [NetBeans](###netbeans-maven)
- [Eclipse](###eclipse-maven)
- [IntelliJ](###intellij-idea-maven)

### NetBeans Maven

- **Primero necesitamos crear un nuevo Proyecto Maven.**

    > ![NetBeans Maven 02](https://i.imgur.com/uOG7LVg.png)
    >
    > En caso de que no esté la carpeta Maven en la librería de proyectos, deberás instalar su soporte a través de los Plugins de NetBeans.
    >
    > ![NetBeans Maven 03](https://i.imgur.com/UGHugJW.png)
    >
    > *Project Name* hace referencia al nombre del proyecto, *Project Localitation* se refiere al lugar en el que guardar nuestro proyecto, todo lo demás son propiedades de Maven que no hace falta cambiar.

- **Editamos el archivo pom.xml de la carpeta Project Files siguiendo las instrucciones señaladas [anteriormente](###version-maven).**

    ![NetBeans Maven 04](https://i.imgur.com/NmYySrm.png)\
    ![NetBeans Maven 05](https://i.imgur.com/yzyFQqh.png)
    > ![NetBeans Maven 06](https://i.imgur.com/oeamGrA.png)
    >
    > Simplemente añadimos el repositorio de JCenter y la dependencia de JDA y JUnit. Además de poner en `<version>` la versión correspondiente al [JDA](https://github.com/DV8FromTheWorld/JDA "JDA Lastest Version").

- **En caso de que el proyecto salte Warning por falta de dependencias locales, bastará con darle click en Resolve Project Problems.**

    ![NetBeans Maven 07](https://i.imgur.com/TOvCjT9.png)
    > ![NetBeans Maven 08](https://i.imgur.com/WyUF2KR.png)
    >
    > Puede ser que este proceso tarde un poco, simplemente hay que esperar que se complete.

- **¡Listo para funcionar!**

### Eclipse Maven

- **Se crea el Proyecto Maven.**

    > ![Eclipse Maven 01](https://i.imgur.com/8TxSbVi.png)
    >
    > En caso de que no salga la carpeta Maven dentro de los proyectos, deberán instalarse sus dependencias a través del administrador de Plugins de Eclipse.
    >
    > ![Eclipse Maven 02](https://i.imgur.com/DgVNHko.png)
    >
    > Deseleccionamos *Use default Workspace location* para elegir de manera personalizada dónde guardar el proyecto.
    >
    > ![Eclipse Maven 03](https://i.imgur.com/pEMjO1Q.png)
    >
    > Usamos *maven-archetype-quickstart* para evitar configuraciones extra que nos dificulten crear el Bot de manera simple.
    >
    > ![Eclipse Maven 04](https://i.imgur.com/IjGSQqX.png)
    >
    > *Group Id* hace referencia al grupo al que pertenece el proyecto, *Artifact Id* se refiere al nombre con el referenciaremos al proyecto.
    > Todo lo demás es recomendado dejarlo como venga por defecto.

- **Editamos el archivo pom.xml del proyecto Maven para añadirle las dependencias necesarias.**

    ![Eclipse Maven 05](https://i.imgur.com/M3HG06B.png)
    > ![Eclipse Maven 06](https://i.imgur.com/wJyte4Q.png)
    >
    > Es posible que el creador de proyectos Maven de Eclipse venga ya con la `<depenedency>` JUnit.
    >
    > ![Eclipse Maven 07](https://i.imgur.com/zRLOelz.png)
    >
    > Tener en cuenta que en la sección `<version>` va la versión de JDA que se esté usando, en este caso era la **3.6.0_362**

- **¡Listo para funcionar!**

### IntelliJ IDEA Maven

- **Lo primero será crear el proyecto Maven con *archetype-quickstart* para evitarnos complicaciones en la configuración del Bot.**

    ![IntelliJ Maven 01](https://i.imgur.com/e0U3cjn.png)
    > ![IntelliJ Maven 02](https://i.imgur.com/Znn3FHP.png)
    >
    > *GroupId* hace referencia al grupo al que pertenecerá el proyecto, mientras que *ArtifactId* se refiere al nombre de este.
    >
    > ![IntelliJ Maven 03](https://i.imgur.com/uGwX9lo.png)
    >
    > Dejamos esta venta por defecto.
    >
    > ![IntellJ Maven 04](https://i.imgur.com/83eGosc.png)
    >
    > *Project Name* indica el nombre del proyecto y *Project location* indica el lugar en el que se guardará dicho proyecto.

- **Editamos el archivo pom.xml del proyecto para añadirle las dependencias necesarias.**

    ![IntelliJ Maven 05](https://i.imgur.com/0oWQS4Q.png)\
    ![IntelliJ Maven 06](https://i.imgur.com/zbpRkHP.png)
    > ![IntelliJ Maven 07](https://i.imgur.com/zmPmgQy.png)
    >
    > En la sección `<version>` se debe poner la versión correspondiendo al JDA que se esté usando.

- **¡Listo para funcionar!**

---

### Versión JAR

Usar las dependencias del tipo JAR es, básicamente, instalar manualmente una librería descargada.

En este caso se necesitarán una serie de JAR que nos provee [JDA](https://github.com/DV8FromTheWorld/JDA "JDA GitHub").

#### Descargas de los JAR

- [JDA Javadoc (3.6.0)](https://github.com/DV8FromTheWorld/JDA/releases/download/v3.6.0/JDA-3.6.0_354-javadoc.jar "API Javadoc")
- [JDA Source (3.6.0)](https://github.com/DV8FromTheWorld/JDA/releases/download/v3.6.0/JDA-3.6.0_354-sources.jar "API Source")
- [JDA (3.6.0)](https://github.com/DV8FromTheWorld/JDA/releases/download/v3.6.0/JDA-3.6.0_354-withDependencies.jar "API Itself")

#### Instalación según el IDE

- [NetBeans](###netbeans-jar)
- [Eclipse](###eclipse-jar)
- [IntelliJ](###intellij-idea-jar)

### NetBeans JAR

- **Primero se deberá crear un proyecto Java.**

    ![NetBeans JAR 01](https://i.imgur.com/aljxbFC.png)
    > ![NetBeans JAR 02](https://i.imgur.com/4Foa9Et.png)
    >
    > Escogemos el nombre del proyecto en *Project Name*, la localización en *Project Location* y decidimos si queremos o no clase **Main** en *Create Main Class*.

- **Una vez creado el proyecto bastará con añadir las librerías a traves del JAR.**

    ![NetBeans JAR 03](https://i.imgur.com/2hd5HxQ.png)\
    ![NetBeans JAR 04](https://i.imgur.com/fXSiKTB.png)

- **Hará falta editar el JAR para incorporar el JavaDoc. Para ello bastará con dar click derecho sobre la librería recién incorporada y click en *Edit...***

    ![NetBeans JAR 05](https://i.imgur.com/aEJgAjg.png)

- **En donde nos pide el *Javadoc* pondremos el JDA-3.x-javadoc.jar, y lo mismo para los *Sources* con JDA-3.x-sources.jar**

    ![NetBeans JAR 06](https://i.imgur.com/edLGRe6.png)

- **¡Listo para funcionar!**

### Eclipse JAR

- **Primero se deberá crear un proyecto Java.**

    ![Eclipse JAR 01](https://i.imgur.com/gACNndm.png)
    > ![Eclipse JAR 02](https://i.imgur.com/KasJd5y.png)
    >
    > En *Project Name* pondremos el nombre de nuestro proyecto Java, mientras que en *Location* escogeremos el lugar donde se guardará.

- **Una vez creado, habrá que añadir las librerías JAR. Para ello damos click derecho sobre el proyecto y click en *Properties*, vamos a *Java Buildpath*, *Libraries* y *Add External JARs...***

    ![Eclipse JAR 03](https://i.imgur.com/Bia74or.png)\
    ![Eclipse JAR 04](https://i.imgur.com/qzvZzY9.png)\
    ![Eclipse JAR 05](https://i.imgur.com/PAFIGMD.png)\
    ![Eclipse JAR 06](https://i.imgur.com/rb8PRTZ.png)

- **Ahora hay que incorporar el *Javadoc* y los *Sources*, para ello debemos dar click derecho en la librería importada y click en *Properties***

    ![Eclipse JAR 07](https://i.imgur.com/cZS7hbc.png)
    
- **En la sección *Java Source Attachment* añadiremos nuestro *JDA-3.x-sources.jda* haciendo click en *External File...***
    
    ![Eclipse JAR 08](https://i.imgur.com/zkElN8Q.png)

- **De igual manera, para añadir el *Javadoc* recurriremos a *Javadoc Location* y haremos click en *Javadoc in archive*, seleccionamos *External file* y ponemos la ruta de nuestro archivo en *Archive path* (Podemos buscar dicha ruta haciendo click en **Browse...**)**

    ![Eclipse JAR 09](https://i.imgur.com/8hOcdrG.png)

- **¡Listo para funcionar!**

### IntelliJ IDEA JAR

- **Lo primero será crear un proyecto Java.**

    ![IntelliJ 01 JAR](https://i.imgur.com/rPwSG3v.png)
    > ![IntelliJ 02 JAR](https://i.imgur.com/i4qipgN.png)
    >
    > En *Project Name* irá el nombre del proyecto Java, mientras que en *Project Location* irá el lugar en el que guardar dicho proyecto.

- **Para añadir las librerías JAR daremos click derecho en el proyecto y click en *Open Module Settings*, iremos a *Dependencies* y añadiremos una de tipo JAR.**

    ![IntelliJ 03 JAR](https://i.imgur.com/dFCt7g4.png)\
    ![IntelliJ 04 JAR](https://i.imgur.com/AnWeWyh.png)\
    ![IntelliJ 05 JAR](https://i.imgur.com/P60eTBe.png)

- **Ahora añadiremos el *Javadoc* y los *Sources*, para ello daremos click derecho sobre la librería añadida y click en *Edit...*. Luego darmeos click en el primer icono `+` y seleccionaremos los otros JAR.**

    ![IntelliJ 06 JAR](https://i.imgur.com/eAvuVcE.png)\
    ![IntelliJ 07 JAR](https://i.imgur.com/uDApmx3.png)
    > ![IntelliJ 08 JAR](https://i.imgur.com/W9l884T.png)
    >
    > Según la versión que se esté usando, los números pueden variar.

    ![IntelliJ 09 JAR](https://i.imgur.com/qZpxwTb.png)

- **¡Listo para funcionar!**

# Dependencias

- JDK 8 o superior:
    - *JDA no es compatible con versiones de Java inferiores a JDK 8.*
    - *El equipo de ScriptHub solo ha testeado JDA hasta JDK10.0.1. No está asegurada su compatibilidad con sistemas superiores.*
- El resto de dependencias deberían ser automáticamente registradas, pero en caso de que no sea así dejo una lista con las dependencias de JDA:
    * NV Websocket Client
        * Version: **2.2**
        * [Github](https://github.com/TakahikoKawasaki/nv-websocket-client)
        * [JCenter Repository](https://bintray.com/bintray/jcenter/com.neovisionaries%3Anv-websocket-client/view)
    * OkHttp
        * Version: **3.8.1**
        * [Github](https://github.com/square/okhttp)
        * [JCenter Repository](https://bintray.com/bintray/jcenter/com.squareup.okhttp:okhttp)
    * Apache Commons Collections4
        * Version: **4.1**
        * [Website](https://commons.apache.org/proper/commons-collections/)
        * [JCenter Repository](https://bintray.com/bintray/jcenter/org.apache.commons%3Acommons-collections4/view)
    * org.json
        * Version: **20160810**
        * [Github](https://github.com/douglascrockford/JSON-java)
        * [JCenter Repository](https://bintray.com/bintray/jcenter/org.json%3Ajson/view)
    * JNA
        * Version: **4.4.0**
        * [Github](https://github.com/java-native-access/jna)
        * [JCenter Repository](https://bintray.com/bintray/jcenter/net.java.dev.jna%3Ajna/view)
    * Trove4j
        * Version: **3.0.3**
        * [BitBucket](https://bitbucket.org/trove4j/trove)
        * [JCenter Repository](https://bintray.com/bintray/jcenter/net.sf.trove4j%3Atrove4j/view)
    * slf4j-api
        * Version: **1.7.25**
        * [Website](https://www.slf4j.org/)
        * [JCenter Repository](https://bintray.com/bintray/jcenter/org.slf4j%3Aslf4j-api/view)

# Ejemplos de Uso

### Ejemplo 1 - Instanciando el Bot

```Java
/* 
 * Haremos que implemente la interfaz EventListener para
 * hacer que esta clase sea capaz de capturar Eventos.
 */
public class NombreApp implements EventListener {

    // Capturamos excepciones
    public static void main(String[] args)
    throws LoginException, RateLimitedException {
        /* 
         * El método .setToken("") nos permite poner entre
         * parámetros el token del bot.
         */
        JDA bot = new JDABuilder(AccountType.BOT).setToken("bot-token").buildAsync();
    }

}
```

### Ejemplo 2 - Capturando Mensajes

```Java
/*
 * Haremos que implemente la interfaz EventListener para
 * que sea capaz de capturar Eventos y que herede de
 * ListenerAdapter para que pueda actuar frente a estos.
 */
public class NombreApp extends ListenerAdapter implements EventListener {

    public static void main(String[] args)
    throws LoginException, RateLimitedException {
        JDA bot = new JDABuilder(AccountType.BOT).setToken("bot-token").buildAsync;
        /*
        * Creamos un nuevo objeto capaz de escuchar, que será
        * nuestro Bot.
        */
        bot.addEventListener(new NombreApp());
    }

    /*
     * Este método heredado de ListenerAdapter capturará
     * cualquier mensaje que el Bot pueda leer.
     */
    @Override
    public void onMessageReceived(MessageReceivedEvent event) {
        String contenidoMensaje = event.getContentDisplay();
        User autorMensaje = event.getAuthor();
        MessageChannel canalMensaje = event.getChannel();

        System.out.println(autorMensaje.getName() + " ha dicho '" + contenidoMensaje + "', en " + canalMensaje.getName());
    }

}
```

### Ejemplo 3 - Enviar Mensajes

```Java
/*
 * Partiendo del ejemplo anterior, solo modificaremos
 * un poco el método onMessageReceived().
 */
@Override
public void onMessageReceived(MessageReceivedEvent event) {
    String contenidoMensaje = event.getContentDisplay();
    User autorMensaje = event.getAuthor();
    MessageChannel canalMensaje = event.getChannel();

    /*
     * Simplemente haremos que el Bot diga "Pong" cuando
     * lea "ping".
     */
    if(contenidoMensaje.equals("ping")) {
        canalMensaje.sendMessage("Pong, " + autorMensaje.getName());
    }
}
```