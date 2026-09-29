# Privacidad del plugin Rezandovoy para Claude

Este documento describe el funcionamiento del plugin Rezandovoy para Claude y
complementa la [política de privacidad general de Rezandovoy](https://rezandovoy.org/politica-de-privacidad).
El responsable del tratamiento es la Compañía de Jesús, Provincia Canónica de
España, Curia Provincial. Sus datos de contacto figuran en esa política.

## Datos que se envían

Cuando una persona usa una herramienta del plugin, Claude envía al servidor MCP
de Rezandovoy los argumentos necesarios para buscar contenido: por ejemplo, un
tema, una fecha o el identificador de una oración. El servidor devuelve datos
del catálogo público y enlaces al audio. No exige una cuenta de Rezandovoy ni
recibe credenciales de acceso a ella.

La skill del plugin pide a Claude que evite solicitar datos identificativos y
que convierta los detalles privados en temas generales antes de buscar. La
persona debe evitar incluir nombres, diagnósticos u otros datos sensibles en
sus peticiones; si los incluye y Claude los usa como argumento de búsqueda,
esos datos pueden llegar al servidor para procesar la consulta.

## Uso y conservación

Rezandovoy usa los argumentos para atender la petición y consultar su propia
API de catálogo. Para `search_prayers`, esa API transmite el texto de búsqueda
a Google Gemini para generar una representación numérica y encontrar oraciones
del catálogo. No guarda el texto de las búsquedas o de la conversación en
una base de datos propia. En la configuración de producción, el registro del
servidor MCP no incluye el contenido de las búsquedas. Se registran datos
técnicos de funcionamiento, como la herramienta llamada, el resultado, la
duración y un identificador de petición; el servidor web puede registrar datos
técnicos de acceso.

El plugin no escribe contenido en la cuenta de Rezandovoy ni modifica su
catálogo. Todas sus herramientas son de solo lectura. El audio se sirve desde
la infraestructura de Rezandovoy mediante una URL temporal cuando está
disponible.

## Servicios implicados

Claude y el alojamiento de las conversaciones son servicios de Anthropic y
están sujetos a sus propias condiciones y política de privacidad. El servidor
MCP y la API de catálogo son infraestructura de Rezandovoy. La búsqueda de
oraciones utiliza además Google Gemini, como indica la
[política de privacidad general](https://rezandovoy.org/politica-de-privacidad).

Para ejercer los derechos de protección de datos sobre la información tratada
por Rezandovoy, consulta la
[política de privacidad general](https://rezandovoy.org/politica-de-privacidad)
o escribe a jesuitas@jesuitas.es.
