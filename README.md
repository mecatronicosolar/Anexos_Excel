# Anexos Excel – Estación de carga solar

Repositorio con los anexos en hoja de cálculo del proyecto de tesis: especificaciones de diseño, resultados del análisis por elementos finitos (FEA) y protocolo de pruebas de la parte mecánica.

## Contenido

| Archivo | Qué contiene | Hojas |
|---|---|---|
| `Especificaciones_Diseños_Teoricos.xlsx` | Especificaciones técnicas, dimensionamiento de baterías y costos de los cuatro diseños (800 W, 3,7 kW, 7 kW y 11 kW). | `Esp. 800W`, `Costos 800W`, `Esp. 3.7kW`, `Costos 3.7kW`, `Esp. 7kW`, `Costos 7kW`, `Esp. 11kW`, `Costos 11kW`, `Revision final` |
| `tablas_FEA_por_potencia.xlsx` | Resultados del FEA en SOLIDWORKS Simulation por estación: von Mises, desplazamiento URES y reacciones para gravedad y cuatro casos de viento. | `800 W`, `3,7 kWp`, `7 kW`, `11 kW` |
| `protocolo_pruebas_mecanica.xlsx` | Protocolo de pruebas M01–M20 (cinco por estación) con condiciones, entradas, salidas esperadas, salidas obtenidas y comentarios. | `Pruebas mecánica`, `Criterios` |

## Convenciones

- **Unidades:** N para fuerzas y reacciones, MPa para von Mises, mm para desplazamientos, kg para masas.
- **Separador decimal:** en algunas celdas de texto de las tablas FEA aparece coma (`−145,62`) y en otras punto (`−145.62`). Los valores numéricos reales deben tomarse siempre de la columna de valores, no del texto.
- **Signos de reacción:** se reportan tal como salen del FEA. En los casos de 180° la reacción horizontal es positiva; en los de 0° es negativa.
- **Columnas `Von Mises` y `Desplazamiento URES` (hojas FEA):** tienen `#VALUE!` como resultado de una fórmula auxiliar. No afectan los valores de las columnas `Valor máximo` y `Valor mínimo`, que son los que se usan.
- **Estación de 7 kW:** su geometría tiene h/L = 1,196, fuera del intervalo de la figura B.6.5-15A de la NSR-10 (0,25 ≤ h/L ≤ 1,00). Sus resultados de viento son exploratorios.

## Cómo se relacionan los archivos

1. Las **especificaciones** definen qué componentes y paneles tiene cada estación.
2. Las **tablas FEA** son los resultados de simulación para esos componentes.
3. El **protocolo de pruebas** compara los resultados del FEA con los valores analíticos del apéndice de cálculos mecánicos y con los criterios de la hoja `Criterios`.

## Criterios de aceptación (protocolo)

- Von Mises máximo ≤ σy / FS_min = 345 / 1,67 ≈ **206,6 MPa** para ASTM A500 Gr C (o 149,7 MPa para ASTM A36 en zonas de placas y cabezales).
- Desplazamiento URES máximo ≤ L/180 (orientativo): 12,2 mm (800 W), 25,7 mm (3,7 kW), 12,8 mm (7 kW) y 25,7 mm (11 kW).

## Pendientes

- Las columnas `Salidas obtenidas` y `Comentarios` del protocolo están vacías y se llenan al ejecutar cada prueba.
- Las capturas de resultados de SOLIDWORKS deben agregarse como evidencia (en comentarios o en una columna nueva).
- Hay valores que no coinciden entre archivos y deben revisarse antes de cerrar el documento (ver abajo).

## Inconsistencias detectadas entre archivos

- **Panel del 3,7 kW:** en las especificaciones aparece JA Solar JAM66D45-**625**/LB (625 W); en el FEA y en el protocolo, JAM66D45 de **620 W**.
- **Nivel del 7 kW y 11 kW:** las especificaciones los clasifican como **Nivel 2**, mientras que el marco teórico y el diseño mecánico sitúan el prototipo en Nivel 1 (≤ 3,7 kW).
- **Número de paneles del 7 kW:** las especificaciones usan **4** Tensite EM710-PH; el diseño mecánico y el FEA usan **2** módulos.
- **Número de paneles del 11 kW:** las especificaciones (hoja `Esp. 11kW`) usan **6** módulos y la hoja `Costos 11kW` usa **5** (5X1). El FEA usa 6.
- **Tensión y fases:** el 800 W usa 110 V monofásico, el 3,7 kW y el 7 kW 220 V, y el 11 kW 380 V trifásico. El marco teórico solo menciona la red monofásica.
- **Baterías del 3,7 kW:** la hoja `Esp. 3.7kW` usa 8 baterías Tensite GEL 12-150 (12 V, 150 Ah), mientras que `Costos 3.7kW` lista 6 baterías de 24 V-200 Ah (banco de 48 V). Revisar cantidad, capacidad, tensión y precio.
