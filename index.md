## Welcome to XShadePage

You can use the [editor on GitHub](https://github.com/nicogc/XShadePage/edit/master/index.md) to maintain and preview the content for your website in Markdown files.


[![IMAGE ALT TEXT HERE](https://img.youtube.com/vi/KoNN6Ii-3r4/0.jpg)](https://www.youtube.com/watch?v=KoNN6Ii-3r4)


Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

## Abstract 
El paper trata de dar un renderizado con
estilo 3D a sketches usando unas curvas usadas en los
sketches llamadas curvas de corte de seccion o CrossSec-  ́
tion Curves, usando estar curvas y algunas restricciones
se puede determinar las normales en el sketch con las
cuales se podr dar un shading adecuado para dar el
efecto de 3D.
## Introduccion
El paper se divide en 2 partes principales, la primera
es encontrar las normales en los puntos de interseccion ́
de los CrossSections y la segunda es propagar esa
normal alrededor de la curva y todo el sketch.

## Algoritmo
### Problema de Minimización

Para hallar las normales en los puntos de interseccion ́ entre cross sections, se intenta minimizar la función para determinar la tercera componente de la tangente
en el punto donde se cruzan las curvas de corte de sección y hallar los valores de las normales correspondientes a los planos 3D que contienen a cada una de las curvas de corte de sección.


## Propagación de la Normal
1. La región esta encerrada por 4 curvas de corte de sección.
2. Se estima una grilla en esta región
3. Por ultimo se utiliza una interpolacion coons en la grilla estimada.

## Implementación
### Leer Cross Sections Curves
En el paper utilizan herramientas de dibujo vecto-
riales estndar, asi que para las curvas que se dibujan

pixel a pixel trato de aproximar una curva de bezier
cubica que minimice la distancia entre esta curva y los
pixeles de la curva y remplazo los pixeles pintados con
la nueva curva de bezier B(t).

### Resolver el problema de minimzación 

Ahora que tenemos las curvas en ya no en pixeles sino en funcin a una curva de bezier podemos saber si
dos curvas se cruzan y en que parametro t, también podemos derivar la funcion de la curva para obtener las  ́
tangentes en esos puntos, pero solo los componentes (x,y).
Para la optimizacion de la función ́ 1 utilice la librería
nlopt, y como era una sumatoria al cuadrado, utilice el metodo de optimización LN_COBYLA que no utiliza
la gradiente de la funcion para poder optimizarla.

## Conclusiones 
Una de las partes más importantes del paper es encontrar las normales en los puntos de interseccion entre cross sections 
curves (Cross Hairs), asi que ahora falta propagar las normales por el sketch.

## Code
Code Available on [GitHub](https://github.com/nicogc/crossshade).


### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

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

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/nicogc/XShadePage/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
