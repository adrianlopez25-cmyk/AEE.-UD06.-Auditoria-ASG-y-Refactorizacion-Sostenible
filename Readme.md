# Auditoría ASG y Refactorización Sostenible

## Indice
1. [Fase 1: Inventario y Dimensión Ambiental (A)](#fase-1-inventario-y-dimensión-ambiental-a)
2. [Fase 2: Dimensión Social y Equidad (S)](#fase-2-dimensión-social-y-equidad-s)
3. [Fase 3: Dimensión de Gobernanza y Ética (G)](#fase-3-dimensión-de-gobernanza-y-ética-g)
4. [Fase 4: Propuesta de Refactorización (Green Coding)](#fase-4-propuesta-de-refactorización-green-coding)

---

## Fase 1: Inventario y Dimensión Ambiental (A)
### 1.1 Medición inicial de la huella de carbono
<img width="1494" height="744" alt="image" src="https://github.com/user-attachments/assets/a80dd3d9-7d7d-4a46-8359-ab87273d291c" />

Como se puede observar en la imagen sobre el analisis en Website Carbon Calculator, la web mkpersons.com ha obtenido una calificación de D. Esto quiere decir que es bastante superior a la media general de webs.

Rendimiento Energético: Aunque el gráfico indica que es "más limpia que el 52% de las webs analizadas", estar en la franja D (en una escala de A+ a F) demuestra que existe un margen de mejora significativo, lo cual intentaremos mejorar como veremos mas adelante en la refactorizacion del codigo.

Respecto al posicionamiento: La web se encuentra justo en el límite de la media global , lo que sugiere que no se han aplicado técnicas de Green Coding o de optimización de activos durante su desarrollo de esta misma, tecnicas las cuales hemos ido aprendiendo durante todo el curso de sostenibilidad.



### 1.2 Identificación de Bloatware
<img width="572" height="932" alt="image" src="https://github.com/user-attachments/assets/308c8adf-eabb-4a72-95d5-cb901474f2a6" />

Segun la imagen, observamos que de media solo llega al 50% es bastante bajo, eso quiere decir que existe un gran desperdicio energetico, ya sea que obliga a trabajar en gran medida al dispositivo del usuario o que están enviando datos que el usuario quizás ni llega a ver.

Todo esto nos hace ver que nuestra web aun le queda mucho margen de mejora ya que lo mas optimo seria llegar al 90%.

<img width="564" height="929" alt="image" src="https://github.com/user-attachments/assets/59d31c9d-746f-4ec6-9b3d-490208f55647" />

Los tres archivos mas pesados de la web son img-2,img-1,img, algo que es bastante obvio ya que las tres imagenes se encuentran el formato JPG ya que este formato requiere mucho recursos, un formato menos pesado como tipo WebP, haria trabajar menos al dispositivo del usuarios, pero esto ya lo tratare mas adelante.


### 1.3 Análisis de "Inflación de Software"
Obviamente si, ya que la puntuación de 50 en Performance indica que el navegador está procesando una cantidad de datos desproporcionada para lo que finalmente muestra en pantalla. Es decir la web posee gran cantidad de: "grasa digital": scripts y estilos que el usuario no necesita.

Consumo de recursos en reposo: La calificación D en Website Carbon confirma que la web es más pesada que la media eficiente. Esto es un síntoma clásico de la inflación: se utilizan frameworks o librerías completas, lo que facilita el trabajo del desarrollador, pero no tiene tan en cuenta el hardware del usuario

Desbalance entre funcionalidad y peso: como hemos analizado en la imagen, se emplean imagenes en formato jpg que son muy pesadas y ralentizan mucho la web además de que tardan mas en cargar sobre todo en dispositivos menos actuales.

---

## Fase 2: Dimensión Social y Equidad (S)
### 2.1 Test de Accesibilidad
<img width="1919" height="977" alt="image" src="https://github.com/user-attachments/assets/c51dd693-ae9b-4829-a874-1e8dab788521" />

El panel muestra un AIM Score de 3.7 sobre 10. Es una puntuación baja. Significa que la página tiene bastantes barreras de accesibilidad que podrían excluir a usuarios con discapacidad o con algun tipo de dificultad. Algunos de los problemas de esto serian:
- Hay imágenes que no tienen una descripción en texto. Las personas ciegas usan "lectores de pantalla" que leen lo que hay en la web, en este caso no podrian saber que hay ahi.
- Hay una imagen que además funciona como enlace no tiene descripción, es decir el usuario al clikear ahi no sabra a donde le llevara este link.
- Tambien existe errores de contraste, es decir, existe texto cuyo color es muy parecido al del fondo.

Pero no todo es malo, lo mas destacable de la web es el buen uso de etiquetas de lenguaje o una estructura de encabezados que ayuda a organizar el contenido.


### 2.2 Identificación de barreras de acceso

Como he comentado anteriormente, el principal problema para personas con discapacidad sera el no tener descripciones en los textos, lo que impide a las personas ciegas conocer que existe esa imagen.

Como segundo problema es que utiliza colores muy similares lo que personas daltonicas tendrian problema con ellos
---

## Fase 3: Dimensión de Gobernanza y Ética (G)
### 3.1 Transparencia y Patrones Oscuros (Dark Patterns)
Tiene total transparencia, puedes aceptar o rechazar todas las cookies sin obligar al usuario a aceptarlas, una vez haces click en que no la aceptas no te vuelven a preguntar mas.

### 3.2 Análisis de datos innecesarios
Piden los datos extricatamente necesarios por si te quieres contactar con ellos como son nombre, telefono, email y que deseas conocer. Tambien cuenta con un CAPTCHA para que no sea un bot el que lo realize de forma automatica y sature la web.

<img width="809" height="643" alt="image" src="https://github.com/user-attachments/assets/1404164f-3c3e-4d1f-a609-7402e9f036cf" />


---

## Fase 4: Propuesta de Refactorización (Green Coding)
### 4.1 Optimización de activos (Assets)
    
Como se ve en la imagen del punto 1.2 Identificación de Bloatware, observe que uno de los principales 
problemas de la web donde mas se utilizan los recursos es que el mayor peso de la web son las imagenes que estan en formato png por lo que una de las mejores opciones seria cambiar esto a formato wepb para que pida menos recursos

### 4.2 Reducción de peticiones y procesamiento
<img width="1898" height="964" alt="image" src="https://github.com/user-attachments/assets/fc683e67-c998-42a4-b0ef-465a1ed79c4d" />

Como se puede observar segun el buscador, el bloque @font-face aparece mas de 160 veces, repitiendo una y otra vez fuentes optimizadas para diferentes User Agents antiguos ( como son Open Sans, Lato,Montserrat que estan adaptados a user agents antiguos como lo serian firefox27, firefox39,safari de daum...etc).

<img width="995" height="503" alt="image" src="https://github.com/user-attachments/assets/2755641b-91a5-41e1-b7cf-ad41956d1a34" />

También se observa que el uso de bloques para Firefox 27/39 o formatos como .woff se siguen empleando pese a que hoy en día, en pleno 2026, ya no son necesarios. En la actualidad, el más utilizado es el formato WOFF2, que se emplea en más del 98% de los casos.

Con todo esto presente, me pregunto: ¿qué podría mejorar? Esto me lleva a diferentes puntos:

Eliminar variantes de fuentes no utilizadas: el código contiene pesos desde el 100 hasta el 900 en formato normal e itálica para cuatro familias distintas. No es necesario en absoluto utilizar tantas variantes, por lo que reduciría esta cantidad de fuentes.

Aplazar scripts de Divi y WordPress: existen archivos como xmlrpc.php que ya están obsoletos y presentan problemas de seguridad. Por ello, lo mejor es deshabilitarlos.


### 4.3 Reflexión sobre la Paradoja de Jevons
Para poder evitar que el éxito anule el ahorro enérgetico lo principal es abordar los siguientes puntos:

1. Arquitectura Jamstack / Generación Estática (SSG): En lugar de que cada nuevo usuario active una consulta a la base de datos PHP de WordPress (consumiendo CPU del servidor), se pre-renderiza la web en HTML estático. El coste energético de servir un archivo plano es infinitamente menor.

2. Caché agresiva en el Edge (CDNs Verdes): Utilizar proveedores como Cloudflare con centros de datos alimentados por energía 100% renovable. Si el 95% de las peticiones se resuelven en la caché del nodo más cercano al usuario, se evita el tráfico innecesario por las redes troncales de internet.

3. Green Web Hosting: Alojar la infraestructura en servidores que certifiquen el uso de energía limpia (PUE < 1.2) o compensación de carbono real. Como por ejemplo como hemos visto en clase seria GreenGeeks, la cual por cada kilovatio hora empleado, devlven tres veces esa cantidad a la red en forma de energía eólica.
