# webreflex

Aplicación inicial de [Reflex](https://reflex.dev/) escrita en Python. El código muestra la pantalla de bienvenida del framework, un selector de modo claro/oscuro, un enlace a su documentación y el logotipo de Reflex. Sirve como base para experimentar con la interfaz; todavía no implementa una aplicación de negocio.

## Tecnologías

- **Reflex 0.6.5**, fijado en [`requirements.txt`](requirements.txt).
- Python para definir componentes, estado y páginas.
- Frontend generado en `.web/`; su manifiesto incluye Next.js 14.2.16 y React 18.3.1.
- Configuración de la aplicación en [`rxconfig.py`](rxconfig.py), con `app_name="webreflex"`.

La clase `State` está vacía y solo se registra la página `index`. No hay persistencia, autenticación ni integraciones de negocio implementadas en el módulo de la aplicación.

## Preparación y ejecución local

Se necesita Git y una versión de Python compatible con Reflex 0.6.5, con soporte para entornos virtuales. El repositorio no fija la versión de Python; Python 3.11 es una opción para evaluar, no una combinación validada aquí. La instalación y el arranque de Reflex pueden necesitar acceso a Internet para preparar las herramientas y dependencias del frontend.

Desde una terminal compatible con Bash:

```bash
git clone git@github.com:tunonalves/webreflex.git
cd webreflex
python3.11 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
reflex run
```

Abrir la dirección del frontend que indique `reflex run` en la terminal. Mantener los servicios de desarrollo limitados al entorno local; esta receta no configura un despliegue público. Detenerlos con `Ctrl+C`.

El proyecto ya contiene `rxconfig.py`, el paquete Python y archivos generados de `.web/`. No es necesario crear una aplicación nueva ni sustituir la página existente por otra plantilla. Si el arranque requiere reinicializar archivos generados, consultar las instrucciones de la versión instalada y revisar el diff antes de conservar esos cambios.

## Uso y desarrollo

1. Editar [`webreflex/webreflex.py`](webreflex/webreflex.py), en particular la función `index()`.
2. Definir los datos y eventos necesarios en `State`; actualmente no hay lógica de estado propia.
3. Registrar nuevas páginas mediante `app.add_page(...)` según las necesidades del proyecto.
4. Guardar imágenes y otros recursos públicos en [`assets/`](assets/).

Usar la aplicación Python como fuente de verdad. `.web/` contiene infraestructura generada del frontend; ejecutar sus scripts de Next.js de forma aislada no sustituye el arranque coordinado por Reflex.

## Estructura

| Ruta | Función |
| --- | --- |
| [`webreflex/webreflex.py`](webreflex/webreflex.py) | Componentes, `State`, instancia `rx.App` y registro de la página |
| [`webreflex/__init__.py`](webreflex/__init__.py) | Inicializador del paquete |
| [`rxconfig.py`](rxconfig.py) | Nombre y configuración de la aplicación |
| [`requirements.txt`](requirements.txt) | Dependencia directa de Reflex |
| [`assets/`](assets/) | Recursos públicos; incluye el favicon |
| [`.web/package.json`](.web/package.json) | Dependencias y scripts del frontend generado |
| [`.web/next.config.js`](.web/next.config.js) | Configuración generada de Next.js |

## Verificación y limitaciones

En el entorno instalado, comprobar la CLI y sus opciones antes de adaptar los comandos:

```bash
reflex --help
reflex run --help
```

No se incluye una suite de pruebas ni un procedimiento de despliegue. Solo se fija la dependencia directa de Reflex; no hay un lockfile de todas sus dependencias transitivas. Las versiones registradas en el repositorio deben revisarse antes de reutilizarlas en un servicio público.

Esta revisión fue estática: se inspeccionaron el módulo Python, la configuración y los manifiestos, sin instalar dependencias ni iniciar Reflex, compilar el frontend o probarlo en un navegador. Por ello, las instrucciones de ejecución no representan una prueba de compatibilidad con el equipo del lector.

## Créditos y licencia

Repositorio de [tunonalves](https://github.com/tunonalves). La pantalla y el texto inicial proceden de la plantilla de bienvenida de Reflex y conservan su logotipo y enlace de documentación. No se incluye una licencia general del proyecto; las dependencias mantienen sus propias licencias.
