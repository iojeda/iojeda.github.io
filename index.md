## Como instalar el Dni-e en Arch Linux fácil y rápido

Requisitos previos

1. Lector de tarjetas inteligentes compatible con Linux
2. Dni-e en vigor y con certificados actualizados
3. Autoridades de Certificación del Dni-e

### 1. Elección del Lector de tarjetas

Hay multiples opciones en este punto, yo os voy a indicar que lector tengo pero cualquier otro con soporte linux os sirve.
Tan solo teneis que aseguraros, al leer los datos del embalaje se indica claramente, que entre los sistemas operativos soportados se encuentra linux.

Mi lector: [Woxter-lector-dnie](http://woxter.es/esp/es/perifericos-pc-/79-woxter-lector-dni-electrnico-8435089008814.html#)

Precio: 11,99€

Esta basado en el siguiente controlador del fabricante Alcor [Alcor AU9540](http://www.alcormicro.com/en_content/c_product/product_01b.php?CategoryID=4&IndexID=4) (esto me lo chivó linux)

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

```markdown
$ sudo pacman -S opensc
```



You can use the [editor on GitHub](https://github.com/iojeda/iojeda.github.io/edit/master/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
$ sudo pacman -S opensc
```

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/iojeda/iojeda.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
