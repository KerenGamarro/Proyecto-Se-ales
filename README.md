# Proyecto-Señales
Objetivos
• Aplicar lo aprendido en la iniciativa académica Procesamiento de Señales para implementar una
unidad de procesamiento de señales.
• Utilizar la aplicación AppDesigner de Matlab para desarrollar la interfaz gráfica (front-end) y la
lógica (back-end) de la unidad de procesamiento.
Duración: 4 semanas
Los estudiantes diseñarán e implementarán una unidad de procesamiento de señales en tiempo real
usando el microcontrolador STM32F446RE (embebido en la placa Nucleo-F446RE) y la aplicación
AppDesigner de Matlab. Trabajarán en parejas (si el número de estudiantes de alguna sección es
impar, habrá un grupo de tres).
Instrucciones
El objetivo del proyecto es implementar una unidad de procesamiento de señales que cuente con un
módulo físico y una interfaz gráfica.
El módulo físico se implementará utilizando la placa Nucleo-F446RE y permitirá a) muestrear señales
analógicas, b) enviar las señales muestreadas a una PC, c) realizar procesamiento/filtrado en tiempo
real de las señales muestreadas y d) mostrar el resultado del procesamiento en un osciloscopio.
La interfaz gráfica se desarrollará por medio de la aplicación AppDesigner de Matlab, y permitirá a)
diseñar distintos filtros y efectos, b) leer las señales provenientes de la placa Nucleo-F446RE, c) cargar
datos/señales pregrabadas de archivos existentes en la PC, d) aplicar el filtro o efecto a la señal y
mostrar gráficos importantes (señal original, señal procesada, espectros de amplitud unilateral,
respuesta en frecuencia, entre otros) y e) configurar los filtros y otros parámetros del módulo físico.
Figura 1. Diagrama de Conexión de Proyecto
El módulo físico deberá permitir al usuario realizar lo siguiente:
• Muestrear señales analógicas por medio del módulo de conversión Analógico/Digital (ADC).
• Aplicar filtros y otros efectos a las señales muestreadas, en tiempo real. Esto debe hacerse por
medio de algoritmos a partir de ecuaciones de diferencias.
• Mostrar el resultado del procesamiento por medio de un convertidor Digital/Analógico (DAC), para
poder observar dichas señales en el osciloscopio.
• Enviar las señales muestreadas (sin procesar) a la PC en donde se esté ejecutando la interfaz gráfica.
• Recibir los parámetros del filtro/efecto que se desea aplicar en tiempo real, provenientes de la
interfaz gráfica. Lo anterior implica que debe haber comunicación de dos vías entre el Nucleo-
F446RE y la PC. Además, implica que los coeficientes de la ecuación de diferencias y el
correspondiente algoritmo que se ejecuta en el Nucleo-F446RE pueden cambiar, sin necesidad de
modificar ni recompilar el programa.
La interfaz gráfica deberá permitir al usuario realizar lo siguiente:
• Obtener datos (señales muestreadas) provenientes del módulo físico “bajo demanda”. El usuario
debe poder solicitar la captura por medio de un botón. La duración de la señal capturada, i.e. la
cantidad de muestras obtenidas debe ser configurable.
• Cargar señales y parámetros relevantes (ej. frecuencia de muestreo) previamente almacenados en
archivos .mat. Se puede asumir que los nombres de las variables contenidas en los archivos son
conocidos (ej. x, Fs).
• Graficar las señales que se muestreen (recibidas del módulo físico) o que se carguen, versus tiempo.
• Seleccionar el tipo de filtro (IIR, FIR) o efecto (ej. eco, distorsión) que se desee aplicar a la señal
muestreada/cargada y modificar sus parámetros, como frecuencias de corte, retraso, etc. (i.e.
diseñar los filtros). Se sugiere usar dropdown menus, switches u otros elementos similares para
seleccionar los tipos de filtros, y usar edit fields numéricos para ingresar los parámetros de interés.
También se sugiere delimitar los rangos para que hagan sentido.
• Mostrar las gráficas de respuesta en frecuencia de los filtros. Se debe dar la opción de graficar la
magnitud en dB o en magnitud adimensional. La escala horizontal debe poderse mostrar en
rad/muestra y Hz.
• Procesar las señales muestreadas/cargadas por medio de los filtros/efectos diseñados, y graficar
las señales filtradas/procesadas en el dominio del tiempo. Si se cambian los filtros/efectos, se debe
poder volver a procesar la señal original, y actualizar la gráfica de la señal procesada.
• Mostrar los espectros de amplitud unilateral de las señales muestreadas/cargadas (original) y las
procesadas. Consideren el uso de plot en lugar de stem, para una mejor visualización (o mejor
aún, dar la opción al usuario del tipo de gráfica deseada). Mostrar la escala horizontal en Hz.
• Generar un archivo .csv con los datos de la señal muestreadas/cargada (original) y la señal
procesada (la más reciente). El nombre del archivo y la ubicación donde se guardará deben poder
ser especificados por el usuario.
• Exportar variables correspondientes a los filtros y otras variables de interés a un archivo .mat, con
un nombre y ubicación especificados por el usuario.
• Diseñar el filtro/efecto que el módulo físico debe implementar, y enviar los parámetros
correspondientes (coeficientes de la ecuación de diferencias) a la placa Nucleo-F446RE, para que
esta actualice su algoritmo.
Pueden encontrar información sobre el desarrollo de interfaces gráficas en Matlab y el AppDesigner en
el siguiente enlace: https://la.mathworks.com/discovery/matlab-gui.html
También pueden buscar otros tutoriales y ejemplos en línea para familiarizarse con la creación de
interfaces gráficas.
Funciones útiles a la hora de abrir o guardar archivos: uigetfile, uigetdir, uiputfile.
Detalles de Implementación y Validación
Pueden usar herramientas y funciones que hayan usado o visto en laboratorios y teoría, y
pueden reciclar código que hayan desarrollado anteriormente. Para el diseño de los filtros, pueden usar
cualquier método visto en clase, y pueden usar herramientas y funciones de Matlab, incluyendo el Filter
Designer. Para aplicar los filtros/efectos en Matlab, pueden usar funciones nativas como filter o
lsim.
El módulo físico debe implementar los filtros/efectos por medio de sus ecuaciones de
diferencias, como se mencionó anteriormente. Restrinjan los filtros a implementar en el módulo físico
a filtros IIR. Deberán asegurarse de que las señales que entren a la Nucleo-F446RE estén en el rango de
amplitud adecuado (entre 0 y 3.3 V). De lo contrario, pueden dañarla.
Para validar su unidad de procesamiento, deberán obtener/generar señales adecuadas para
usarlas como entradas. Deberán diseñar experimentos para verificar el correcto funcionamiento de
cada módulo de su unidad:
• Para el módulo físico, pueden usar el generador de funciones, circuitos analógicos, sensores,
dispositivos biomédicos o cualquier otro que genere señales de voltaje que se puedan conectar a
la Nucleo-F446RE.
• Para evaluar el correcto diseño de sus filtros/efectos y la funcionalidad de la interfaz gráfica, se
recomienda hacer pruebas con señales artificiales creadas con componentes/bandas de frecuencia
específicas. Luego, ya pueden probar su unidad con señales “reales”, como señales de audio,
señales bioeléctricas, etc.
Características adicionales (opcional, para crédito extra – máximo 10%)
Adicional a los requisitos descritos anteriormente, tendrán la oportunidad de implementar
características adicionales para puntos extra. Las siguientes son algunas posibilidades:
• Visualización continua de las señales capturadas en la interfaz gráfica. Pueden agregar un modo
de captura y visualización continua, adicional al modo “bajo demanda”. Para cambiar entre uno
y otro modo pueden usar switches u otros elementos en la interfaz.
• Variación de la frecuencia de muestreo del módulo físico desde la interfaz gráfica. La interfaz
podría tener un campo para ingresar la frecuencia de muestreo deseada, la cual se enviaría al
Nucleo-F446RE. El programa de la Nucleo-F446RE necesitaría reconfigurar el temporizador
luego de recibir el parámetro.
• Cargar señales almacenadas en archivos de texto y/o .csv. Además de poder cargar datos desde
archivos .mat, la interfaz permitiría cargar señales y parámetros relevantes desde otro tipo de
archivos.
• Reproducir señales de audio. Además de procesar señales de audio y visualizarlas en las distintas
gráficas en tiempo y frecuencia, pueden incluir botones para reproducir los audios originales y
los procesados. Pueden usar funciones nativas de Matlab para ello.
• Si tienen otras ideas, las pueden discutir con su instructor de laboratorio.
Importante: Antes de implementar las características adicionales, deben asegurarse de completar los
requisitos obligatorios. Si implementan características adicionales sin un funcionamiento completo
del resto del proyecto, no se tomarán en cuenta en la nota final.
Los grupos de tres estudiantes deberán implementar obligatoriamente una característica adicional.
Evaluación
Demostración del módulo físico: 30%
Se verificará que el módulo físico pueda realizar todas las tareas indicadas.
Demostración de la interfaz gráfica: 35%
Se verificará que la interfaz ofrezca todas las opciones indicadas.
Vídeo demostrativo: 15%
Cada grupo deberá generar un vídeo demostrando la funcionalidad de su unidad de procesamiento. El
vídeo debe durar un máximo de 8 minutos.
Código: 10%
Deberán entregar su proyecto de STM32CubeIDE de la Nucleo-F446RE y de Matlab, debidamente
comentados e identificados. Deben incluir todo lo necesario para hacer funcionar su unidad de
procesamiento.
Importante: cualquier evidencia de plagio detectada en el código implicará una nota de cero para todos
los involucrados.
Asistencia y trabajo durante las sesiones: 10%
Todos deben asistir a las sesiones de laboratorio. En las sesiones se darán indicaciones y sugerencias
para el proyecto, y se resolverán dudas. Además, se espera que cada grupo muestre avances parciales.
Por cada ausencia no justificada se deducirán puntos del proyecto (de forma individual).
Nota: Se espera que trabajen en el proyecto fuera de las sesiones de laboratorio. Hay mucho que se
puede hacer en casa (sin el equipo de laboratorio). Sin embargo, si se organizan bien y trabajan
eficientemente durante las sesiones, no deberían necesitar invertir demasiado tiempo fuera.
Demostración y entrega:
La demostración de los proyectos se deberá hacer en la semana 19 del ciclo (18 al 22 de mayo) durante
la sesión regular de laboratorio.
Tendrán 2 días luego de la fecha límite de presentación para subir un archivo .zip o .rar a Canvas. El
archivo comprimido deberá incluir todos sus programas (de Matlab y de la Nucleo-F446RE). Además,
deberán subir el video demostrativo.
Tanto el archivo .zip/.rar como el video deberán ser subidos en la tarea de Canvas correspondiente.
Dado a que Canvas sólo permite entregar un tipo de archivo por vez, deberán presentar el archivo
.zip/.rar y el video en diferentes intentos.
Nombren a su archivo comprimido así: IE3032_Proyecto_Apellido1_Apellido2.zip (o .rar) o
BE3022_Proyecto_Apellido1_Apellido2.zip (o .rar). Los apellidos deben estar en orden alfabético. Si el
grupo es de tres personas, incluyan los tres apellidos, por supuesto.
Ejemplos: IE3032_Proyecto_Castillo_Rivera_Zea.zip, BE3022_Proyecto_Esquit_Kellner.rar.
Sólo un miembro del grupo deberá subir el archivo comprimido y el video. Se bajarán puntos si los
dos o tres estudiantes suben archivos, y si el vídeo dura más de 8 minutos.
