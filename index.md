## Como instalar el Dni-e en Arch Linux fácil y rápido

Requisitos previos

1. Lector de tarjetas inteligentes compatible con Linux
2. Dni-e en vigor y con certificados actualizados
3. Autoridades de Certificación del Dni-e

### 1.- Elección del Lector de tarjetas

Hay multiples opciones en este punto, yo os voy a indicar que lector tengo pero cualquier otro con soporte Linux os sirve.
Tan solo teneis que aseguraros, al leer los datos del embalaje se indica claramente, que entre los sistemas operativos soportados se encuentra Linux.

**Mi lector**: [Woxter-lector-dnie](http://woxter.es/esp/es/perifericos-pc-/79-woxter-lector-dni-electrnico-8435089008814.html#)

**Precio**: 11,99€

Esta basado en el siguiente controlador del fabricante Alcor [Alcor AU9540](http://www.alcormicro.com/en_content/c_product/product_01b.php?CategoryID=4&IndexID=4) ( esto me lo chivó Linux :smile: )

```markdown

$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 003 Device 005: ID 058f:9540 Alcor Micro Corp. AU9540 Smartcard Reader
Bus 003 Device 002: ID 046d:c326 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
$

```

### 2.- Dni-e en vigor y con certificados actualizados

Ademas de comprobar que el Dni-e no este caducado aqui tenemos que tener en cuenta alguna cosilla mas...

Modificar la clave que indicamos en la creación del Dni-e para validar las gestiones realizadas con el mismo ( si, yo tampoco me acordaba :smile: )

Comprobar que los certificados instalados en el chip de la tarjeta estan al día o Renovarlos en su caso.

Estas labores pueden realizarse en cualquier comisaría de policía donde tengan esta maquina: [Punto de Actualizacin del Dnie](https://www.dnielectronico.es/img/PAD.jpg)

### 3.- Instalar Autoridades de Certificación del Dni-e en el Navegador Web

Hay que descargar los certificados de la pagina oficial de la policía: [Dnie AC Certs](https://www.dnielectronico.es/PortalDNIe/PRF1_Cons02.action?pag=REF_077)

En esta pagina se ofrecen tanto el certificado sha-256 como el sha-1 (por motivos de compatibilidad).
Es desaconsejable instalar los certificados sha-1 ya que los navegadores y otras empresas (entre otros Microsoft) han dejado de confiar en ese tipo de certificados los cuales ya no son admitidos a partir del 01/01/2017

Pueden ampliar información [aqui](https://www.tbs-certificates.co.uk/FAQ/en/microsoft_depreciation_sha1.html)

Una vez han bajado los certificados toca instalarlos en el navegador. Yo utilizo Firefox, asi que os diré como se instala para este navegador.

Vamos a: **Preferencias --> Avanzadas --> Ver Certificados --> Autoridades --> Importar**
Entonces elegimos el certificado que nos hemos bajado y listo.

### 4.- Instalar Software y añadir modulo de control en Firefox

Ahora toca lo divertido :smile:

Vamos a instalar el software necesario para el control del lector de tarjetas inteligente,todos los paquetes necesarios estan en los repositorios oficiales por tanto no necesitaremos tirar de [AUR](https://aur.archlinux.org/)
Los paquetes necesarios son los siguientes:

**opensc**     --> librerias y herramientas para lectores de tarjetas Inteligentes

**ccid**       --> driver genérico USB para lectores de tarjetas Inteligentes

**pcsc-tools** --> Arquitectura PC/SC para tarjetas Inteligentes

### Instalar paquetes
```markdown
$ sudo pacman -S opensc ccid pcsc-tools
```

### Instalar y arrancar servicio controlador
```markdown
$ sudo systemctl enable pcscd.service
$ sudo systemctl start pcscd.service
```

### Instalar modulo controlador en Firefox

Abrimos Firefox

Vamos a: **Preferencias --> Avanzadas --> Dispositivos de Seguridad**

Luego pulsamos en el boton **Load**

Se nos abrirá una nueva ventana donde pondremos como nombre el nombre identificativo que queramos para el modulo (Ej: Dnie o SmartCard) y como fichero pulsamos browse y elegimos **/usr/lib/opensc-pkcs11.so**

Ya tenemos todo configurado, ahora solo tenemos que reiniciar Firefox para empezar a disfrutar de las ventajas de la era digital :smile:, eso si, desde la libertad y serenidad que te ofrece el mundo Linux.

Un saludo y hasta la proxima aventura :wink:
