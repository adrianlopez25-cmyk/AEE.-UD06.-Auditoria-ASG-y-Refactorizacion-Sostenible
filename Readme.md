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


### 2.2 Identificación de barreras de acceso


---

## Fase 3: Dimensión de Gobernanza y Ética (G)
### 3.1 Transparencia y Patrones Oscuros (Dark Patterns)


### 3.2 Análisis de datos innecesarios


---

## Fase 4: Propuesta de Refactorización (Green Coding)
### 4.1 Optimización de activos (Assets)


### 4.2 Reducción de peticiones y procesamiento


### 4.3 Reflexión sobre la Paradoja de Jevons
