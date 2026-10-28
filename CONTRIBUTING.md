# Guía de trabajo colaborativo

Este documento explica cómo trabajamos en equipo con Git y GitHub en el proyecto **VendeYa**.

## 1. Configuración inicial (solo una vez)

1. Acepta la invitación de colaborador que llegó a tu correo o en <https://github.com/notifications>.
2. Configura tu identidad en Git con el **mismo correo de tu cuenta de GitHub** (así tus commits cuentan en tu perfil):

   ```bash
   git config --global user.name "Tu Nombre"
   git config --global user.email "tu-correo@ejemplo.com"
   ```

3. Clona el repositorio e instala las dependencias:

   ```bash
   git clone https://github.com/MrGameOver7/VendeYa.git
   cd VendeYa
   npm install
   ```

## 2. Flujo de trabajo (GitHub Flow)

La rama `main` siempre debe funcionar. Nadie sube cambios directamente a `main`: cada tarea se hace en su propia rama y se integra con un Pull Request.

```bash
git checkout main
git pull                                  # trae lo último
git checkout -b feature/nombre-de-la-tarea
# ... programa y prueba tus cambios ...
npm run typecheck                         # verifica que no haya errores de tipos
git add .
git commit -m "feat: descripción corta del cambio"
git push -u origin feature/nombre-de-la-tarea
```

Luego entra a GitHub, crea el **Pull Request** hacia `main` y asigna como revisor al coordinador (@MrGameOver7).

### Nombres de ramas

| Prefijo | Uso | Ejemplo |
| --- | --- | --- |
| `feature/` | Nueva funcionalidad | `feature/exportar-cuadre` |
| `fix/` | Corrección de errores | `fix/vuelto-negativo` |
| `docs/` | Documentación | `docs/informe-avance-1` |
| `design/` | Cambios visuales | `design/colores-tickets` |

### Mensajes de commit

Usamos el formato *Conventional Commits*: `tipo: descripción en presente`.

- `feat: agrega filtro por categoría en catálogo`
- `fix: corrige cálculo de stock al vender por kilo`
- `docs: actualiza README con capturas`
- `style: ajusta espaciado de la pantalla de ajustes`

## 3. Responsables por módulo

| Integrante | Usuario | Módulos / tareas |
| --- | --- | --- |
| Marines Quincho Rony | @MrGameOver7 | Arquitectura, navegación, estado global (`src/store`), Venta y Revisar Orden, revisión de PRs |
| Cajusol Bustamante José Antonio | @Cajusol11 | Requerimientos, Inventario y formulario de producto |
| Huamán Ventura Milton | @Roger282002 | Diseño UI/UX, componentes (`src/components`), Catálogo y Ajustes |
| Terrones Navarro Juan Alexis | @Alexisterron | Pruebas, Historial y Cuaderno de fiados, documentación |

## 4. Reglas del equipo

- Antes de empezar una tarea, crea o asígnate un **Issue** en GitHub.
- Haz `git pull` antes de crear tu rama para evitar conflictos.
- No subas la carpeta `node_modules` ni archivos con contraseñas.
- Prueba tus cambios en Expo Go antes de abrir el Pull Request.
