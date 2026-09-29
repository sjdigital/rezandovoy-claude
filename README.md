# Rezandovoy para Claude

![Icono de Rezandovoy](.claude-plugin/icon.png)

Complemento de Claude que combina una skill de acompañamiento con el servidor
MCP remoto de Rezandovoy:

`https://apinueva.rezando.es/mcp/claude`

Rezandovoy es un proyecto de la Compañía de Jesús Provincia de España. El
repositorio técnico se publica desde SJDigital.

No instala ni despliega otro backend. El mismo MCP sirve el catálogo y los
audios a ChatGPT, Claude y otros clientes compatibles con Streamable HTTP.

## Qué permite hacer

- Escuchar la oración de hoy o la correspondiente a una fecha.
- Encontrar oraciones para una situación, emoción o celebración.
- Abrir una oración concreta.
- Descubrir series de oración.
- Mostrar siempre el enlace directo al audio cuando está disponible.

## Instalación rápida como conector personalizado

En Claude, abre **Customize > Connectors**, pulsa **Add custom connector** e
introduce:

`https://apinueva.rezando.es/mcp/claude`

Este camino activa las herramientas, pero no instala la skill de acompañamiento
incluida en el complemento.

## Instalación del complemento

Sube el ZIP de este directorio desde **Customize > Plugins > Add > Upload plugin**.
Después, abre la pestaña **Connectors** del complemento y conecta el servidor
Rezandovoy. En organizaciones Team o Enterprise, un propietario también puede
distribuirlo mediante un marketplace interno.

Una vez instalado, habilita Rezandovoy en la conversación y prueba:

- «Quiero escuchar la oración de hoy».
- «Busca una oración para agradecer la vida».
- «Quiero una oración para mi cumpleaños».
- «Enséñame una serie para preparar la Pascua».

## Compatibilidad del audio

El MCP devuelve una URL HTTPS directa en `audio_url` y ofrece una tarjeta MCP Apps
con reproductor. La presentación de la tarjeta depende del cliente; la skill
incluye siempre un enlace de audio visible para los casos en que no aparezca.

## Privacidad

El complemento envía al MCP de Rezandovoy únicamente los criterios necesarios
para localizar el contenido solicitado. No requiere una cuenta de Rezandovoy.
La skill indica a Claude que generalice los detalles personales antes de una
búsqueda y que no solicite información identificativa innecesaria.

Política de privacidad:
https://rezandovoy.org/politica-de-privacidad

Detalles del tratamiento en Claude:
https://github.com/sjdigital/rezandovoy-claude/blob/main/PRIVACY.md

Soporte: soporte@rezandovoy.com

Documentación: este README y la guía de uso de la skill `skills/rezar/SKILL.md`.

La licencia MIT cubre únicamente los archivos de este complemento. Los
contenidos, imágenes y audios servidos por Rezandovoy conservan sus derechos
propios.

## Desarrollo y validación

La configuración MCP utiliza el transporte HTTP recomendado para servidores
remotos:

```json
{
  "mcpServers": {
    "rezandovoy": {
      "type": "http",
      "url": "https://apinueva.rezando.es/mcp/claude"
    }
  }
}
```

Antes de publicar una versión, valida el directorio con:

```bash
claude plugin validate . --strict
```

También deben probarse individualmente las cuatro herramientas del MCP mediante
MCP Inspector y mediante un conector personalizado de Claude.

## Publicación

Este directorio está preparado para ser la raíz del repositorio público
`sjdigital/rezandovoy-claude`. No publiques el directorio padre ni copies
secretos, archivos `.env` o código del servidor de Rezandovoy.

La publicación en el directorio de Claude tiene dos envíos en el
[portal de desarrolladores](https://claude.ai/directory/manage):

1. Envía el MCP remoto `https://apinueva.rezando.es/mcp/claude` como **MCP connector**.
2. Envía el repositorio público de este complemento como **Plugin bundle**.

Ambos envíos deben hacerse desde la misma organización para poder asociar sus
fichas. Anthropic valida y revisa los componentes antes de publicarlos. El
repositorio puede ser privado durante la revisión, pero debe ser público antes
de que el complemento aparezca en el directorio. El conector también debe
probarse con MCP Inspector y como conector personalizado de Claude.
