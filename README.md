# VendeYa 🛒

**VendeYa** es una aplicación móvil de punto de venta (POS) para bodegas y minimarkets. Permite vender escaneando el código de barras de los productos con la cámara del celular, cobrar con efectivo, Yape, Plin, tarjeta o crédito ("fiado"), controlar el inventario y revisar el cuadre de caja del día, sin necesidad de una computadora ni conexión a Internet.

> Proyecto del curso **Programación de Aplicaciones Móviles** – Facultad de Ingeniería de Sistemas y Mecánica Eléctrica (UNTRM).

## Funcionalidades

| Módulo | Qué permite hacer |
| --- | --- |
| **Venta** | Escanear códigos de barras con la cámara (con linterna y pausa), ingresar códigos manualmente, armar el carrito y modificar cantidades. |
| **Revisar Orden** | Aplicar descuentos, agregar notas, elegir el método de pago (Efectivo con cálculo de vuelto, Yape/Plin con QR, Tarjeta POS, Crédito/fiado) y emitir el ticket. |
| **Ticket** | Ver el comprobante de la venta y compartirlo por WhatsApp u otras apps. |
| **Catálogo** | Vender sin escáner tocando productos en una grilla filtrada por categoría y búsqueda. |
| **Inventario** | Ver indicadores (productos, valor del inventario, stock bajo, agotados), registrar/editar productos, generar códigos internos y ajustar stock (entradas y mermas). |
| **Historial** | Cuadre de caja por periodo (hoy, semana, mes, todo), desglose por método de pago, lista de tickets y **Cuaderno de fiados** con registro de abonos. |
| **Ajustes** | Datos del negocio (logo, RUC, dirección, mensaje del ticket), moneda, métodos de pago con QR de Yape/Plin y categorías. |

## Tecnologías

- [React Native](https://reactnative.dev/) 0.86 + [Expo](https://expo.dev/) SDK 57
- TypeScript
- Expo Router (navegación basada en archivos: pestañas + pila)
- expo-camera (lectura de códigos de barras EAN-13, EAN-8, UPC, Code128, QR)
- expo-image-picker (logo y QR de pago)
- Zustand + AsyncStorage (estado global persistente en el dispositivo, funciona sin Internet)

Plataforma objetivo: **Android** (el código también es compatible con iOS).

## Estructura del proyecto

```
src/
├── app/                    # Pantallas (Expo Router)
│   ├── _layout.tsx         # Navegación raíz (Stack)
│   ├── (tabs)/             # Barra inferior de pestañas
│   │   ├── index.tsx       # Venta
│   │   ├── catalogo.tsx
│   │   ├── inventario.tsx
│   │   ├── historial.tsx   # Tickets + cuaderno de fiados
│   │   └── ajustes.tsx
│   ├── orden.tsx           # Revisar orden / cobro
│   ├── producto/[id].tsx   # Nuevo / editar producto
│   └── ticket/[id].tsx     # Detalle del ticket
├── components/             # Componentes reutilizables (UI, escáner, filas)
├── store/useStore.ts       # Estado global y lógica de negocio
├── data/seed.ts            # Datos de ejemplo
├── theme/colors.ts         # Paleta de colores
├── types/                  # Tipos TypeScript
└── utils/                  # Formatos, fechas, ticket
```

## Cómo ejecutar el proyecto

Requisitos: [Node.js](https://nodejs.org/) 20 o superior y la app **Expo Go** (compatible con SDK 57) en un celular Android.

```bash
git clone https://github.com/MrGameOver7/VendeYa.git
cd VendeYa
npm install
npx expo start
```

Escanea el código QR que aparece en la terminal con la app Expo Go. El celular y la PC deben estar en la misma red Wi-Fi (si no, usa `npx expo start --tunnel`).

Comandos útiles:

```bash
npm run typecheck   # verificación de tipos con TypeScript
npx expo-doctor     # diagnóstico de dependencias
```

Para generar un APK instalable se usará EAS Build: `npx eas-cli@latest build -p android --profile preview`.

## Equipo de desarrollo

| Integrante | Usuario de GitHub | Rol |
| --- | --- | --- |
| Marines Quincho Rony (líder) | [@MrGameOver7](https://github.com/MrGameOver7) | Coordinador y desarrollador React Native |
| Cajusol Bustamante José Antonio | [@JoseCajusol](https://github.com/JoseCajusol) | Analista de requerimientos y desarrollador |
| Huamán Ventura Milton | [@Roger282002](https://github.com/Roger282002) | Diseñador UI/UX y desarrollador |
| Terrones Navarro Juan Alexis | [@Alexisterron](https://github.com/Alexisterron) | Responsable de pruebas (QA) y documentación |

¿Quieres contribuir? Revisa la guía de trabajo colaborativo en [CONTRIBUTING.md](CONTRIBUTING.md).

## Licencia

Distribuido bajo la licencia MIT. Ver [LICENSE](LICENSE).
