# 📄 Documentación técnica  
💻 **Laboratorio 1 – Tecnologías Web Modernas**  

**Nombre:**  Eyden Su Díaz
**Carné:**  2023025837
**Curso:** IC-8057 – Introducción al Desarrollo de Páginas Web  
**Fecha:**  8/8/2025

---

## 1. Frameworks de desarrollo web
### a. ¿Qué es un framework y qué problema resuelve?

Un framework es como una estructura que proporciona una base para el proceso de desarrollo de aplicaciones. Los frameworks ayudan a evitar **escribir todo desde cero**. Ofrecen un conjunto de herramientas y elementos que ayudan a agilizar el proceso de desarrollo. Actúa como una plantilla que puede usarse e incluso modificarse para cumplir con los requisitos del proyecto.

Ejemplo:
   Angular es un framework de código abierto basado en **TypeScript**. Fue creado y es mantenido por **Google**. Angular ofrece muchas funciones y servicios que pueden ayudar en el desarrollo de sitios web y Aplicaciones Web Progresivas (PWA). Permite la **integración de herramientas de terceros**. Muchas empresas de primer nivel utilizan el framework Angular, como Google, PayPal, Nike, Upwork, entre otras.

### b. Arquitectura general y enfoque (MVC, SPA, SSR, etc.)

Para desarrollar cualquier aplicación web, Angular sigue los patrones de diseño MVC (Model-View-Controller) y MVVM (Model-View-ViewModel), lo que facilita un **enfoque estructurado** y organizado para el diseño de la aplicación, además de hacer más sencilla la gestión del código, mejorar la **mantenibilidad**, etc.

### c. Ejemplo práctico documentado  
- **Estructura de proyecto**  

Para un sistema de punto de venta, se puede tener la siguiente estructura:

```
src
└── app
    ├── core
        ├── layout
        ├── auth
            ├── auth-store.ts
            ├── auth-store.spec.ts
            ├── auth.model.ts
            ├── auth-guard.ts
            ├── auth-guard.spec.ts
            ├── auth.routes.ts
            └── pages
                ├── login
                ├── register
                ├── password-recovery
        ├── services
            └── notification-api.ts
            └── notification-api.spec.ts
        ├── interceptors
            └── api-interceptor.ts
            └── api-interceptor.spec.ts
    └── features
        ├── product
        ├── cart
        ├── checkout
            ├── checkout-api.ts
            ├── checkout-api.spec.ts
            ├── checkout.model.ts
            ├── checkout-guard.ts
            ├── checkout-guard.spec.ts
            ├── checkout.routes.ts
            └── pages
                ├── address
                ├── payment
    └── shared
        ├── components
            ├── notification.ts
            ├── notification.spec.ts
            ├── notification.html
            ├── notification.css
        ├── pipes
            ├── date-pipe.ts
            ├── date-pipe.spec.ts
        ├── utils
            ├── array.utils.ts
            ├── array.utils.spec.ts
```

- **Fragmento de código comentado**  

```typescript
// src/app/shared/components/notification.ts

import { Component, Input } from '@angular/core';

@Component({
  selector: 'app-notification',
  templateUrl: './notification.html',
  styleUrls: ['./notification.css']
})
export class NotificationComponent {
  @Input() message: string = '';
  @Input() type: 'success' | 'error' | 'info' = 'info';
  isVisible: boolean = false;

  show(message: string, type: 'success' | 'error' | 'info' = 'info') {
    this.message = message;
    this.type = type;
    this.isVisible = true;

    // Ocultar automáticamente después de 3 segundos
    setTimeout(() => this.hide(), 3000);
  }

  hide() {
    this.isVisible = false;
  }
}
```

### d. Comparación breve entre al menos dos frameworks

En la siguiente tabla se comparan Angular y React Js

| Característica | Angular | React.js |
| ------------------------- | ----------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| **Tipo**                  | Framework completo de código abierto basado en TypeScript. | Biblioteca de JavaScript para construir interfaces de usuario. |
| **Desarrollador**         | Google. | Meta (Facebook). |
| **Lenguaje base**         | TypeScript (con HTML y CSS). | JavaScript (con JSX). |
| **Arquitectura / Patrón** | MVC y MVVM. | Basado en componentes, patrón unidireccional de datos. |
| **Tipo de aplicaciones**  | SPA, PWA y aplicaciones empresariales grandes y estructuradas. | Interfaces de usuario interactivas, SPA y aplicaciones móviles (con React Native). |
| **Curva de aprendizaje**  | Más pronunciada por su complejidad y cantidad de conceptos. | Más sencilla para principiantes, aunque puede volverse compleja con librerías externas. |
| **Ventajas**              | Estructura sólida, muchas herramientas integradas, ideal para proyectos grandes, soporte oficial de Google. | Alta flexibilidad, gran comunidad, reusabilidad de componentes, rápido rendimiento con Virtual DOM. |
| **Desventajas**           | Mayor tamaño inicial, más rígido y menos flexible que React. | Necesidad de librerías adicionales para funcionalidades como enrutamiento o gestión de estado avanzado. |
| **Empresas que lo usan**  | Google, PayPal, Nike, Upwork. | Facebook, Instagram, Netflix, Airbnb.|

---

## 2. Control de versiones y trabajo colaborativo
### a. ¿Qué es el control de versiones y por qué es esencial?

Control de versiones es un software utilizado para rastrear revisiones, resolver conflictos de integración en el código y gestionar los diferentes artefactos involucrados en proyectos de software (por ejemplo, diseño, datos, imágenes). Esto permite una comunicación fluida, el manejo de cambios y la reproducibilidad entre desarrolladores y otros miembros del equipo.

### b. Conceptos clave  
- Repositorio: Es un lugar para almacenar código, archivos y el historial de revisiones de cada archivo. Los repositorios pueden tener múltiples colaboradores y pueden ser públicos o privados.

- Commit: Un commit graba los cambios de uno o mas archivos en una rama (branch).

- Branch: Son espacios de trabajo aislados que permiten experimentar, construir y probar cambios sin afectar al código principal. Son como tener varias versiones de un proyecto ejecutándose una al lado de la otra, cada una con su propio historial de cambios.

- Merge: Es un comando utilizado para combinar los cambios de dos ramas en una. Integra trabajos de diferentes ramas en una única historia unificada sin perder avances. 

- Pull Request: Un pull request es una petición que el propietario de un fork (copia de un repo) de un repositorio hace al propietario del repositorio original para que este último incorpore los commits que están en el fork.

### c. Flujos de trabajo comunes  
- Git Flow
Es un modelo alternativo de creación de ramas en Git en el que se utilizan ramas de función y varias ramas principales.

![Git Flow](/static/img/gitflow_example.svg)

Este flujo de trabajo utiliza dos ramas para registrar el historial del proyecto. La rama main almacena el historial de publicación oficial y la rama develop o de desarrollo sirve como rama de integración para las funciones. 

Todas las funciones nuevas deben residir en su propia rama, las ramas feature utilizan la rama develop como rama primaria. Cuando una función está terminada, se vuelve a fusionar en develop. **Las funciones no deben interactuar nunca directamente con main.**

![Git Flow with Feature branches](/static/img/gitflow_example_02.svg)

- Trunk-Based  
Es un tipo de control de versiones en la que los desarrolladores fusionan pequeñas actualizaciones de forma frecuente en un "tronco" o rama principal. Dado que esta práctica simplifica las fases de fusión e integración, ayuda a lograr la CI y la CD ([¿Qué es CI/CD y por qué se usa en desarrollo web?](#a-qué-es-cicd-y-por-qué-se-usa-en-desarrollo-web)) y, al mismo tiempo, aumenta la entrega de software y el rendimiento de la organización.
Es una práctica obligatoria para la integración continua. Si los procesos de desarrollo y pruebas están automatizados, pero los desarrolladores trabajan en ramas de función aisladas y largas que se integran con poca frecuencia en una rama compartida, no se está aprovechando todo el potencial de la integración continua.

![Git Flow](/static/img/trunk_based.jpg)


- Feature Branches  
Es un flujo de trabajo basado en ramas dedicadas para el desarrollo de nuevas funcionalidades.  
Cada nueva característica o corrección se desarrolla en su propia rama independiente, separada de la rama principal (`main` o `develop`), lo que permite trabajar de forma aislada sin afectar el código estable.
Este enfoque es compatible con otros modelos como **Git Flow** o **Trunk-Based**, ya que se centra en el patrón de creación de ramas más que en la organización de todo el repositorio.
**Ventajas:**
- Permite desarrollo paralelo entre distintos miembros del equipo.  
- Facilita las revisiones de código mediante *Pull Requests*.  
- Reduce el riesgo de introducir errores en la rama principal.  
- Mejora la trazabilidad de cambios específicos.
**Flujo de trabajo típico:**
1. Crear una rama a partir de la rama base (`main` o `develop`):
   ```bash
   git checkout -b feature/nombre-de-la-funcionalidad develop
   ```
2. Realizar los commits correspondientes durante el desarrollo.
3. Enviar la rama al repositorio remoto para respaldo o colaboración:

   ```bash
   git push origin feature/nombre-de-la-funcionalidad
   ```
4. Abrir una *Pull Request* para revisión y aprobación.
5. Fusionar la rama en la base cuando la funcionalidad esté lista y aprobada.
6. Eliminar la rama de la funcionalidad para mantener el repositorio limpio.

### d. Ejemplo de uso de Git en un proyecto  
- Inicialización  

1. Crear un nuevo repositorio local:
   ```bash
   git init
   ```

2. Configurar nombre de usuario y correo (solo necesario la primera vez):

   ```bash
   git config --global user.name "Su Nombre"
   git config --global user.email "su.email@ejemplo.com"
   ```

- Commits  

1. Agregar archivos al área de preparación (*staging*):

   ```bash
   git add archivo.txt
   ```

   O agregar todos los archivos:

   ```bash
   git add .
   ```
2. Guardar los cambios con un mensaje descriptivo:

   ```bash
   git commit -m "Descripción breve del cambio"
   ```

- Ramas  

1. Crear una nueva rama:

   ```bash
   git branch nombre-de-la-rama
   ```
2. Cambiar a la nueva rama:

   ```bash
   git checkout nombre-de-la-rama
   ```

   *(En versiones recientes de Git se puede crear y cambiar en un solo paso)*:

   ```bash
   git switch -c nombre-de-la-rama
   ```
3. Subir la rama al repositorio remoto:

   ```bash
   git push origin nombre-de-la-rama
   ```
4. Fusionar la rama en la principal (`main` o `develop`):

   ```bash
   git checkout main
   git merge nombre-de-la-rama
   ```

> 💡 **UN TIP:** Siempre es bueno usar mensajes de commit claros y significativos para mantener un historial entendible.

### e. Herramientas recomendadas  
- GitHub
  Plataforma de alojamiento de repositorios Git más popular.  
  Ofrece integración con CI/CD, gestión de proyectos, revisiones de código y una gran comunidad de desarrolladores.  
  Ideal para proyectos de código abierto y privados.  
  🌐 [https://github.com](https://github.com)
- GitLab  
  Plataforma completa que incluye repositorios Git, integración continua, despliegue automatizado y gestión de incidencias en un solo lugar.  
  Puede usarse en la nube o instalarse en servidores propios (*self-hosted*).  
  🌐 [https://gitlab.com](https://gitlab.com)
- Bitbucket 
  Herramienta de Atlassian que permite trabajar con Git y Mercurial (aunque Mercurial fue descontinuado en 2020).  
  Ofrece integración directa con Jira y Trello, así como pipelines de CI/CD.  
  Soporta repositorios privados ilimitados en su plan gratuito.  
  🌐 [https://bitbucket.org](https://bitbucket.org)

---

## 3. Autenticación y seguridad moderna
### a. Conceptos  
- Autenticación: Es el proceso que usan las empresas para confirmar que solo las personas, servicios y aplicaciones adecuados con los permisos correctos pueden acceder a recursos de la organización. 
- Autorización  
La autorización es el proceso para dar a alguien la capacidad de acceder a un recurso.
- Tokens: La autenticación basada en tokens es un protocolo de autenticación en el que los usuarios verifican su identidad a cambio de un token de acceso único. Los usuarios pueden entonces acceder al sitio web, la aplicación o el recurso durante la vida del token sin tener que volver a introducir sus credenciales.
- JWT: Es un estándar abierto de la industria utilizado para transmitir información de forma segura entre dos partes, normalmente entre un **cliente** (por ejemplo, el frontend de una aplicación) y un **servidor** (backend).  
Un JWT contiene un objeto **JSON** con los datos o “claims” (reclamos) que se desean compartir.  
Cada token está firmado criptográficamente mediante algoritmos de **hashing** para asegurar su integridad, evitando que su contenido sea modificado por el cliente o por terceros maliciosos.  
Este mecanismo es ampliamente usado para **autenticación** y **autorización** en aplicaciones web modernas.
- OAuth: Significa *“Open Authorization”* (autorización abierta) y es un estándar diseñado para permitir que un **sitio web** o **aplicación** acceda a recursos alojados por otras aplicaciones web **en nombre de un usuario**.  
Este protocolo es ampliamente utilizado para integraciones con servicios como **Google, Facebook, GitHub, Twitter**, entre otros.

### b. Diagrama de flujo explicativo del proceso de autenticación con JWT

![JWT Diagram](/static/img/JWT_Diagram.webp)

1. **Inicio de sesión**

   * El usuario envía sus credenciales al servidor mediante una solicitud (`request`) a `"/auth"`.

2. **Verificación y generación de token**

   * El servidor verifica las credenciales.
   * Si son correctas, genera un JWT firmado y lo envía al cliente.

3. **Almacenamiento del token**

   * El navegador guarda el JWT (en *localStorage* o *sessionStorage*).

4. **Acceso a recursos protegidos**

   * En cada nueva solicitud, el cliente envía el JWT en la cabecera de autorización.

5. **Validación y respuesta**

   * El servidor verifica la firma del JWT y, si es válido, procesa la solicitud y envía la respuesta.



### c. Buenas prácticas en seguridad web

1. **Inicio de sesión:** El usuario envía sus credenciales al servidor (`/auth`).  
2. **Verificación y generación:** El servidor valida las credenciales y genera un JWT firmado.  
3. **Almacenamiento:** El navegador guarda el JWT.  
4. **Acceso a recursos:** El cliente envía el JWT en cada nueva solicitud.  
5. **Validación y respuesta:** El servidor verifica el token, procesa la petición y envía la respuesta.

### d. Aplicaciones reales en plataformas modernas

1. **Google APIs**  
   - Utiliza **OAuth 2.0** para que aplicaciones de terceros accedan de forma segura a recursos como Gmail, Drive o Calendar sin compartir la contraseña del usuario.  
   - Los tokens de acceso suelen ser **JWT** con información codificada y firmada.  

2. **Auth0**  
   - Plataforma de autenticación como servicio que implementa **OAuth 2.0** y **OpenID Connect**.  
   - Genera y gestiona **JWT** para autenticar usuarios y autorizar el acceso a APIs.  

3. **Firebase Authentication**  
   - Servicio de Google que permite autenticar usuarios mediante correo/contraseña, redes sociales o proveedores externos.  
   - Emite **JWT firmados** para identificar al usuario en las peticiones a la base de datos y funciones en la nube.  

---

## 4. Gestores de contenido desacoplados (Headless CMS)

### a. Definición: Headless CMS vs CMS tradicional

Un **CMS tradicional** conecta directamente el *back-end* (base de datos y panel de administración) con el *front-end* (donde se muestra el contenido). Esto facilita a editores y administradores realizar cambios visuales sin conocimientos técnicos avanzados. Hay que decir que esta estrecha relación entre contenido y diseño limita la flexibilidad: normalmente el contenido solo se entrega a un sitio web y se debe usar el lenguaje de programación nativo del CMS, dificultando su escalabilidad y uso en múltiples plataformas.  

Un **Headless CMS** es un repositorio de contenido que lo expone mediante una **API**, sin acoplarlo al *front-end*. Esto lo hace independiente del lenguaje de programación, permitiendo entregar el mismo contenido a sitios web, apps móviles, *wearables* y otros sistemas desde una sola fuente. Al separar contenido y código, facilita el trabajo en equipo remoto, la integración con control de versiones, pruebas automatizadas y prácticas de entrega continua, logrando mayor agilidad y escalabilidad.

### b. Arquitectura basada en APIs

En un **Headless CMS**, el contenido se gestiona y almacena en el servidor, pero se entrega a través de una **API** (REST o GraphQL) a cualquier cliente que lo solicite.  
- **Flujo básico**:  
  1. El editor crea y guarda el contenido en el CMS.  
  2. El CMS expone ese contenido en formato JSON o similar.  
  3. El *frontend* (web, app, etc.) consume la API y renderiza la información.  

Esta arquitectura desacoplada permite que un mismo conjunto de datos se utilice en múltiples canales sin duplicar esfuerzos ni código.

### c. Ventajas, limitaciones y casos de uso comunes

**Ventajas**  
- Entrega de contenido a múltiples dispositivos y plataformas.  
- Independencia del lenguaje de programación en el *frontend*.  
- Mayor flexibilidad para integrar con servicios externos.  
- Escalabilidad y facilidad para trabajo colaborativo remoto.  

**Limitaciones**  
- Requiere conocimientos de desarrollo para implementar el *frontend*.  
- No incluye un sistema visual integrado para construir el sitio final.  
- Puede aumentar la complejidad de la infraestructura.  

**Casos de uso comunes**  
- Sitios web multicanal y multilingües.  
- Aplicaciones móviles que consumen contenido dinámico.  
- Proyectos con necesidad de entregar contenido a dispositivos IoT o *wearables*.  
- Integraciones con sistemas empresariales (ERP, CRM, etc.).

### d. Ejemplo de conexión del frontend a un CMS headless
### b. Arquitectura basada en APIs  

En un **Headless CMS**, el contenido se gestiona y almacena en el servidor, pero se entrega a través de una **API** (REST o GraphQL) a cualquier cliente que lo solicite.  
- **Flujo básico**:  
  1. El editor crea y guarda el contenido en el CMS.  
  2. El CMS expone ese contenido en formato JSON o similar.  
  3. El *frontend* (web, app, etc.) consume la API y renderiza la información.  

Esta arquitectura permite que un mismo conjunto de datos se utilice en múltiples canales sin duplicar esfuerzos ni código.

---

### c. Ventajas, limitaciones y casos de uso comunes  

**Ventajas**  
- Entrega de contenido a múltiples dispositivos y plataformas.  
- Independencia del lenguaje de programación en el *frontend*.  
- Mayor flexibilidad para integrar con servicios externos.  
- Escalabilidad y facilidad para trabajo colaborativo remoto.  

**Limitaciones**  
- Requiere conocimientos de desarrollo para implementar el *frontend*.  
- No incluye un sistema visual integrado para construir el sitio final.  
- Puede aumentar la complejidad de la infraestructura.  

**Casos de uso comunes**  
- Sitios web multicanal y multilingües.  
- Aplicaciones móviles que consumen contenido dinámico.  
- Proyectos con necesidad de entregar contenido a dispositivos IoT o *wearables*.  
- Integraciones con sistemas empresariales (ERP, CRM, etc.).

---

### d. Ejemplo de conexión del frontend a un CMS headless  

**Ejemplo con JavaScript usando `fetch` para consumir un API REST de un Headless CMS**:

```javascript
// URL de la API del Headless CMS
const API_URL = 'https://api.ejemplo-cms.com/posts';

// Obtener contenido del CMS
async function obtenerContenido() {
  try {
    const respuesta = await fetch(API_URL);
    const datos = await respuesta.json();

    // Renderizar en el DOM
    const contenedor = document.getElementById('contenido');
    contenedor.innerHTML = datos.map(post => `
      <article>
        <h2>${post.titulo}</h2>
        <p>${post.descripcion}</p>
      </article>
    `).join('');
  } catch (error) {
    console.error('Error al obtener el contenido:', error);
  }
}

// Llamar a la función
obtenerContenido();
```
---

## 5. Pasarelas de pago en aplicaciones web

### a. ¿Qué es una pasarela de pago? ¿Qué rol cumple en una aplicación moderna?
 Es una plataforma tecnológica que actúa como intermediaria en las transacciones económicas electrónicas. Permite que las empresas físicas y en línea acepten, procesen y gestionen diversos métodos de pago (tales como tarjetas de crédito, tarjetas de débito o monederos digitales) de forma segura y eficiente. 

### b. Requisitos comunes  
- Cuenta de comercio  
  Para procesar pagos, generalmente se necesita una cuenta de comercio o cuenta mercantil vinculada a la pasarela, que permite recibir fondos de los clientes.

- Seguridad  
  Las pasarelas deben cumplir con estándares de seguridad como PCI DSS (Payment Card Industry Data Security Standard) para proteger los datos sensibles de los usuarios.

- Integración técnica  
  Se requiere que la pasarela ofrezca APIs o SDKs que faciliten su integración con la aplicación web, ya sea para pagos con tarjetas, billeteras digitales u otros métodos.

### c. Ventajas y limitaciones de integrar pagos en línea

**Ventajas**  
- **Seguridad mejorada**: uso de cifrado, tokenización y autenticación multifactor para proteger datos sensibles.  
- **Variedad de métodos de pago**: tarjetas de crédito/débito, ACH, pagos en tiempo real, carteras digitales, métodos alternativos y criptomonedas.  
- **Integración optimizada**: APIs y páginas de pago alojadas que simplifican la conexión con múltiples procesadores sin aumentar el alcance de PCI.  
- **Flexibilidad y escalabilidad**: posibilidad de gestionar qué métodos de pago ofrecer según el perfil del cliente y expandirse a nuevos canales fácilmente.  
- **Facilidad para negocios de suscripción**: soporte para facturación recurrente e integración con software de gestión de suscripciones.

**Limitaciones**  
- **Tarifas por transacción**: cargos por autorización, incluso si el pago es rechazado, que pueden afectar la rentabilidad.  
- **Pérdida de datos y falta de reportes**: algunas pasarelas limitan el acceso a datos sin procesar y análisis avanzados.  
- **Dependencia del proveedor**: compatibilidad condicionada por la plataforma de comercio electrónico o el adquirente.  
- **Complejidad en soluciones personalizadas**: desarrollo e implementación costosos y que requieren mantenimiento constante.  



### d. Comparación entre pasarelas  
| Pasarela | Facilidad de integración | Tarifas | Métodos de pago soportados | Soporte local | Características destacadas |
|----------|--------------------------|---------|----------------------------|---------------|---------------------------|
| **Stripe** | Muy buena, con SDKs para múltiples lenguajes | Competitivas | Tarjetas, Apple Pay, Google Pay, transferencias | Limitado en algunos países | Soporte para suscripciones, pagos recurrentes, webhooks |
| **TiloPay** | Moderada, con enfoque regional | Variables según volumen | Tarjetas, transferencias locales, pagos en efectivo | Fuerte en América Latina | Soluciones para e-commerce y marketplaces |
| **Bancos** | Depende del banco, suele ser más complejo | Generalmente más altos | Principalmente tarjetas | Local y regional | Integración directa con cuentas bancarias, seguridad confiable |

---

## 6. Automatización del despliegue y hosting moderno
### a. ¿Qué es CI/CD y por qué se usa en desarrollo web?

**CI/CD** son siglas que representan dos prácticas fundamentales en el desarrollo de software moderno:

- **CI (Integración Continua)**: Es la práctica de integrar regularmente (varias veces al día o con cada cambio) el código desarrollado por diferentes programadores en un repositorio centralizado. Cada integración se verifica automáticamente mediante pruebas para detectar errores lo antes posible.

- **CD (Entrega Continua o Despliegue Continuo)**: Es la automatización del proceso de entrega del software, ya sea para preparar una versión lista para producción (entrega continua) o incluso desplegar automáticamente los cambios en el entorno productivo (despliegue continuo).

Se usan en el desarrollo web porque:
- **Reducción de errores**: Al integrar y probar continuamente, se detectan fallos rápidamente, lo que mejora la calidad del software.

- **Entrega rápida de funcionalidades**: Permite llevar nuevas características o correcciones al usuario final de forma ágil y frecuente.

- **Automatización de procesos**: Disminuye el trabajo manual repetitivo en compilación, pruebas y despliegues, aumentando la eficiencia.

- **Mejor colaboración**: Facilita que equipos distribuidos puedan trabajar en paralelo sin generar conflictos de integración.

### b. Hosting estático vs dinámico

**Hosting estático** entrega archivos HTML, CSS y JS tal cual, sin procesamiento en el servidor. Es rápido, económico y seguro, ideal para sitios simples como portafolios o páginas informativas. Ejemplos: GitHub Pages, Netlify.

**Hosting dinámico** permite generar contenido en tiempo real usando lenguajes de servidor y bases de datos. Ofrece personalización y funcionalidades avanzadas, pero requiere más recursos y es más complejo. Ejemplos: AWS, DigitalOcean, Heroku.

¿Cuál es mejor elegir?
Se recomienda usar un hosting estático para sitios con contenido fijo y pocas actualizaciones. Por otro lado, es mejor usar el hosting dinámico si es necesario contenido personalizado o funcionalidades complejas.

### c. Flujo de despliegue automatizado

El flujo de despliegue automatizado es un proceso que permite publicar cambios en un sitio web de forma rápida y sin intervención manual constante. Generalmente sigue estos pasos:

Commit: Los desarrolladores suben cambios al repositorio de código (por ejemplo, Git).

Integración Continua (CI): El sistema automáticamente construye y prueba el código para asegurar que no haya errores.

Entrega Continua (CD): Si las pruebas pasan, el sistema despliega automáticamente el sitio al servidor o plataforma de hosting.

Este flujo agiliza el lanzamiento de actualizaciones, reduce errores humanos y garantiza que el sitio esté siempre actualizado y funcionando correctamente.

### d. Documentar el proceso seguido para desplegar la parte 2 del laboratorio

### Cómo desplegar un proyecto en Netlify

1. **Crear cuenta en Netlify**
   Registráte gratis en [Netlify](https://app.netlify.com).

2. **Agregar un nuevo sitio**
   Al ingresar, hay que dar clic en “Add A New Project”.

3. **Conectar con tu repositorio Git**
   Luego, vincular Netlify con GitHub, GitLab u otro proveedor compatible para que pueda acceder al código.

4. **Autorizar Netlify**
   Se debe permitir que Netlify acceda a la cuenta de Git para gestionar el despliegue.

5. **Seleccionar repositorio**
   Seguidamente, seleccionar el repositorio que contiene el sitio web.

6. **Desplegar el sitio**
   Netlify hará la compilación y desplegará el proyecto automáticamente.

7. **Acceder al sitio publicado**
   Cuando termine, se obtiene la URL pública del sitio.

---

## 📎 Créditos y referencias
## Fuentes y Referencias

- [What is a Framework? – GeeksforGeeks](https://www.geeksforgeeks.org/blogs/what-is-a-framework/)  
- [Angular Architecture Overview – GeeksforGeeks](https://www.geeksforgeeks.org/angular-js/explain-the-architecture-overview-of-angular/)  
- [Angular Folder Structure Guide – Angular.Courses](https://www.angular.courses/blog/angular-folder-structure-guide)  
- [Angular RealWorld Example App – GitHub](https://github.com/gothinkster/angular-realworld-example-app/tree/main/src/assets)  
- [Angular vs React – Kinsta](https://kinsta.com/blog/angular-vs-react/)  
- [What is Git Version Control? – GitLab](https://about.gitlab.com/topics/version-control/what-is-git-version-control/)  
- [About Repositories – GitHub Docs](https://docs.github.com/en/repositories/creating-and-managing-repositories/about-repositories)  
- [About Commits – GitHub Docs](https://docs.github.com/en/pull-requests/committing-changes-to-your-project/creating-and-editing-commits/about-commits)  
- [About Branches – GitHub Docs](https://docs.github.com/es/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches)  
- [Qué son las Git Branches – Hostinger](https://www.hostinger.com/es/tutoriales/como-usar-git-branch#%C2%BFQue_son_las_Git_branches)  
- [Git Merge – GeeksforGeeks](https://www.geeksforgeeks.org/git/git-merge/)  
- [¿Qué es un Pull Request? – AprendeGit](https://aprendegit.com/que-es-un-pull-request/)  
- [Gitflow Workflow – Atlassian](https://www.atlassian.com/es/git/tutorials/comparing-workflows/gitflow-workflow)  
- [Trunk-Based Development – Atlassian](https://www.atlassian.com/es/continuous-delivery/continuous-integration/trunk-based-development)  
- [Atlassian – Feature Branch Workflow](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow)  
- [¿Qué es Autenticación? – Microsoft Security](https://www.microsoft.com/es-es/security/business/security-101/what-is-authentication)  
- [¿Qué es Autorización? – Auth0](https://auth0.com/es/intro-to-iam/what-is-authorization)  
- [Token-Based Authentication – Entrust](https://www.entrust.com/es/resources/learn/what-is-token-based-authentication)  
- [¿Qué es JWT? – Supertokens](https://supertokens.com/blog/what-is-jwt)  
- [Adding JWT Authentication to React – Clerk](https://clerk.com/blog/adding-jwt-authentication-to-react)  
- [Application Security Best Practices – Security Compass](https://www.securitycompass.com/blog/application-security-best-practices/)  
- [Headless CMS vs Traditional CMS – Contensis](https://www.contensis.com/community/blog/headless-cms-vs-traditional-cms)  
- [Payment Gateways 101 – Stripe](https://stripe.com/es/resources/more/payment-gateways-101)  
- [Pros and Cons of Gateway Payment Processing – Revolv3](https://www.revolv3.com/resources/pros-and-cons-of-gateway-payment-processing-for-enterprises)  
- [CI/CD DevOps Articles – GitHub](https://github.com/resources/articles/devops/ci-cd)  
- [What is CI/CD? – GeeksforGeeks](https://www.geeksforgeeks.org/devops/what-is-ci-cd/)  
- [Static vs Dynamic Website – Wix Blog](https://www.wix.com/blog/static-vs-dynamic-website)  
- [A Step-by-Step Guide: Deploying on Netlify](https://www.netlify.com/blog/2016/09/29/a-step-by-step-guide-deploying-on-netlify/)  