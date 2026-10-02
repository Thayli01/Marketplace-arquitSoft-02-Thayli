# Enfoque arquitectónico: Clean Architecture

| Elemento | Descripción aplicada al Marketplace |
|---|---|
| Patrón / enfoque arquitectónico | Clean Architecture (Arquitectura Limpia). |
| Objetivo | Separar responsabilidades y controlar las dependencias hacia el dominio. |
| ¿Qué problema resuelve? | Evita el acoplamiento entre la interfaz Angular, las reglas del negocio y las tecnologías externas, como bases de datos, API y servicios de pago. |
| Capas definidas | Presentación, Aplicación, Dominio e Infraestructura. |
| Beneficios | Facilita el mantenimiento y las pruebas unitarias. Permite cambiar implementaciones técnicas sin modificar innecesariamente las reglas del negocio. Mejora la organización y separación de responsabilidades del código. |

## Organización de las capas

| Carpeta | Capa | Contenido en el Marketplace |
|---|---|---|
| `dominio/` | Domain | Entidades Producto, Carrito y Pedido, y los puertos (interfaces) RepositorioProductos, ProcesadorPagos y NotificadorCliente. |
| `aplicacion/` | Application | Casos de uso: ConsultarCatalogo, AgregarAlCarrito y RegistrarCompra. |
| `presentacion/` | Presentación | Componentes Angular: catálogo, carrito y estado del carrito. |
| `infraestructura/` | Infraestructura | Adaptadores que implementan los puertos: repositorio HTTP, procesador de pagos simulado y notificador. |

## Regla de dependencia
1. El dominio no importa nada de las demás capas ni de Angular, HttpClient o RxJS.
2. Los casos de uso solo conocen entidades y puertos del dominio.
3. Los adaptadores de infraestructura implementan los contratos definidos en el dominio (inversión de dependencias).
4. Cambiar de tecnología implica cambiar el adaptador y su registro en `app.config.ts`, no el dominio.

## Relación con el estilo arquitectónico
Este diagrama muestra la organización interna del frontend Angular. El diagrama de `estilo-arquitectonico.md` muestra el backend (monolito modular). Son dos vistas del mismo sistema, conectadas por la API REST.

