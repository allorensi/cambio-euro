# Cambio Euro

Conversor de euros a otras divisas con los tipos de referencia oficiales del Banco Central Europeo (BCE), obtenidos de la API gratuita [Frankfurter](https://frankfurter.dev/es/).

**Web:** https://allorensi.github.io/cambio-euro/

## Funcionalidades

### Conversor
- Escribe un importe en euros y elige la divisa de destino en el desplegable.
- El resultado se calcula al momento, mientras escribes.
- El botón **⇅** invierte la conversión: pasa de la divisa elegida a euros.
- Acepta decimales con coma (`1.250,50`) o con punto (`1250.50`).
- Debajo del resultado se muestra el tipo aplicado (por ejemplo, `1 EUR = 1,1181 USD`) y el nombre completo de la divisa.

### Gráfico histórico
- Muestra la evolución del euro frente a la divisa elegida.
- Periodos disponibles: **1M** (un mes), **3M** (tres meses) y **1A** (un año).
- Indica la variación en el periodo (▲ sube / ▼ baja) en porcentaje, junto con los valores mínimo y máximo.

### Lista de todas las divisas
- Muestra el valor de 1 EUR en todas las divisas que publica el BCE (unas 30).
- Tiene un buscador por código (`USD`) o por nombre (`Dollar`).
- Al pulsar una divisa de la lista, pasa a ser la divisa del conversor y del gráfico.

### Otros detalles
- **Actualización automática:** la página comprueba si hay datos nuevos cada 5 minutos, sin necesidad de recargar.
- **Indicador de estado:** en la cabecera se ve la fecha de los tipos cargados. El punto verde indica que los datos se han cargado bien, el amarillo que se están actualizando y el rojo que no hay conexión con la API (se reintenta solo).
- **Recuerda tus preferencias:** la última divisa elegida, el sentido de la conversión y el periodo del gráfico se guardan en el navegador.
- **Modo claro y oscuro:** se adapta automáticamente al tema del sistema.
- **Adaptada al móvil:** funciona en pantallas pequeñas.
- **Accesible con teclado:** todos los controles se pueden usar con Tab, Enter y Espacio.

## De dónde salen los datos

La página usa la API pública de Frankfurter, que no necesita clave ni registro:

| Uso | Endpoint |
|---|---|
| Tipos actuales | `https://api.frankfurter.dev/v1/latest?base=EUR` |
| Nombres de las divisas | `https://api.frankfurter.dev/v1/currencies` |
| Histórico para el gráfico | `https://api.frankfurter.dev/v1/AAAA-MM-DD..?base=EUR&symbols=USD` |

**Importante:** son los tipos de referencia del BCE, que se publican **una vez cada día laborable, hacia las 16:00 CET**. No son cotizaciones al minuto como las de un mercado de divisas. Los fines de semana y festivos se muestran los tipos del último día publicado.

## Estructura del proyecto

Todo está en un único archivo, sin dependencias ni proceso de compilación:

```
index.html   → HTML, estilos (CSS) y lógica (JavaScript)
README.md    → este documento
```

Las tipografías (Geist y Geist Mono) se cargan desde Google Fonts.

## Uso en local

Basta con abrir `index.html` en el navegador. Si prefieres servirlo con un servidor local:

```bash
python -m http.server 5173
```

y abre http://localhost:5173.

## Publicación

La web se publica con **GitHub Pages** desde la rama `main`. Cualquier cambio que se suba a `main` se publica automáticamente en uno o dos minutos.

## Créditos

- Datos: [Banco Central Europeo](https://www.ecb.europa.eu/) a través de [Frankfurter](https://frankfurter.dev/es/).
