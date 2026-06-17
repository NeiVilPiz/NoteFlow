# Fundamentos de React Native

## React Native vs Aplicaciones Nativas

Una aplicación nativa se desarrolla utilizando las herramientas oficiales de cada plataforma:

* Android → Kotlin o Java
* iOS → Swift u Objective-C

Estas aplicaciones interactúan directamente con los componentes del sistema operativo.

React Native adopta un enfoque diferente. La lógica de la aplicación se escribe en JavaScript o TypeScript utilizando React, pero los componentes visuales no se renderizan como HTML dentro de un navegador.

Por ejemplo:

```tsx
<View>
  <Text>Hola mundo</Text>
</View>
```

Cuando React Native ejecuta este código:

* En Android genera vistas nativas de Android.
* En iOS genera vistas nativas de iOS.

Esto permite reutilizar gran parte del código entre plataformas manteniendo una apariencia y comportamiento nativos.

### Ventajas

* Una única base de código para Android e iOS.
* Desarrollo más rápido.
* Amplio ecosistema basado en React.
* Menor coste de mantenimiento.

### Desventajas

* Dependencia de la capa de comunicación entre JavaScript y código nativo.
* Algunas funcionalidades avanzadas requieren módulos nativos.
* El rendimiento puede verse afectado si el hilo de JavaScript se bloquea.

---

## Arquitectura de React Native

React Native funciona mediante la comunicación entre dos partes principales:

### JavaScript Thread

Es donde se ejecuta:

* La lógica de negocio.
* Los hooks de React.
* El manejo del estado.
* Las peticiones a APIs.
* La navegación.

### UI Thread

Es el hilo nativo del sistema operativo encargado de:

* Dibujar componentes.
* Gestionar animaciones.
* Procesar eventos táctiles.

Ambos hilos deben comunicarse constantemente.

Si el JavaScript Thread se bloquea por operaciones pesadas, la interfaz deja de responder temporalmente porque no puede procesar nuevas instrucciones.

Por esta razón es importante evitar cálculos costosos en el hilo principal y optimizar los renders.

---

## ¿Qué es Metro Bundler?

Metro es el empaquetador (bundler) oficial de React Native.

Su función es:

* Analizar las dependencias del proyecto.
* Empaquetar todos los archivos JavaScript y TypeScript.
* Transformar el código para que pueda ejecutarse en dispositivos móviles.
* Gestionar el Hot Reload y Fast Refresh durante el desarrollo.

Cuando ejecutamos:

```bash
npx expo start
```

Expo inicia Metro automáticamente.

### Funciones principales de Metro

* Resolución de módulos.
* Compilación de TypeScript.
* Fast Refresh.
* Generación del bundle JavaScript.
* Optimización para desarrollo y producción.

Sin Metro, React Native no podría convertir el código fuente en algo ejecutable por la aplicación móvil.

---

## Expo Go

Expo Go es una aplicación instalada en el dispositivo móvil que permite ejecutar proyectos Expo sin generar una compilación propia.

Proceso:

1. Iniciamos el servidor de desarrollo.
2. Escaneamos el código QR.
3. Expo Go descarga el bundle generado por Metro.
4. La aplicación se ejecuta inmediatamente.

### Ventajas

* Configuración extremadamente rápida.
* No requiere Android Studio ni Xcode.
* Ideal para aprendizaje y prototipado.

### Limitaciones

Expo Go únicamente incluye un conjunto predefinido de módulos nativos.

No es posible añadir:

* Módulos nativos personalizados.
* SDKs específicos de terceros.
* Integraciones avanzadas de plataforma.

---

## ¿Por qué Expo Go no es suficiente en proyectos reales?

En aplicaciones profesionales suelen utilizarse funcionalidades como:

* Notificaciones push avanzadas.
* Biometría.
* Bluetooth.
* Integraciones con SDKs externos.
* Cámaras especializadas.
* Servicios nativos personalizados.

Estas funcionalidades requieren código nativo adicional.

Para ello se utilizan los Development Builds.

### Development Build

Un Development Build es una versión personalizada de la aplicación generada específicamente para nuestro proyecto.

Se crea normalmente mediante:

```bash
eas build --profile development
```

A diferencia de Expo Go:

* Incluye nuestras dependencias nativas.
* Permite probar exactamente el entorno real de la aplicación.
* Es la opción utilizada en proyectos profesionales.

Por este motivo, Expo Go suele utilizarse únicamente durante las primeras fases de desarrollo, mientras que los Development Builds son la solución habitual en aplicaciones reales.
