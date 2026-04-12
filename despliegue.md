# 📄 Despliegue Técnico - PokeDex

## 📌 Introducción

En este documento se describe el proceso técnico completo para el despliegue de la aplicación web PokeDex utilizando Azure Static Web Apps. Se detallan las etapas de configuración, construcción, control de versiones, despliegue en la nube y resolución de problemas.

---

# 🧱 1. Clonación del repositorio base

Se utilizó Git Bash para clonar el repositorio proporcionado por el docente:

```bash id="7r8v3l"
git clone https://github.com/rcuello/ac4dem1a.git
cd ac4dem1a
```

---

# 📁 2. Ubicación del proyecto

Se accedió a la ruta donde se encuentra la aplicación:

```bash id="d52o3n"
cd sistemas-distribuidos/poke-dex-lab/source/pokedex-angular
```

---

# ⚙️ 3. Instalación de dependencias

Se instalaron las dependencias necesarias para ejecutar el proyecto Angular:

```bash id="9z0d3y"
npm install
```

---

# 🏗️ 4. Compilación del proyecto

Se generó la versión optimizada para producción:

```bash id="m2t6x8"
npx ng build
```

Esto creó la carpeta:

```text id="xq4z0c"
dist/pokedex-angular/
```

La cual contiene los archivos estáticos necesarios para el despliegue.

---

# 📦 5. Preparación del artefacto de despliegue

Se accedió a la carpeta final:

```bash id="3nv0mk"
cd dist/pokedex-angular
```

Se verificó la estructura:

```bash id="m1x1w8"
ls
```

Se eliminó el historial previo de Git:

```bash id="p4f2a9"
rm -rf .git
```

---

# 🔗 6. Inicialización y conexión con GitHub

```bash id="1k9z7r"
git init
git remote add origin https://github.com/cesar092912121/pokedex-cesar.git
```

---

# 📤 7. Subida del proyecto

```bash id="7o2w9h"
git add .
git commit -m "deploy limpio pokedex"
git branch -M main
git push --set-upstream origin main --force
```

---

# ☁️ 8. Creación del recurso en Azure

Se utilizó Azure Static Web Apps con la siguiente configuración:

* Nombre: pokedex-cesar
* SKU: Free
* Región: East US 2
* Origen: GitHub
* Repositorio: pokedex-cesar
* Rama: main

---

# ⚙️ 9. Configuración de despliegue

Parámetros utilizados:

```text id="9c1v5x"
App location: /
API location: (vacío)
Output location: /
```

Dado que la aplicación ya estaba compilada, no fue necesario ejecutar procesos adicionales de build en Azure.

---

# 🔄 10. Integración continua (CI/CD)

Azure configuró automáticamente un workflow de GitHub Actions que permite:

1. Detectar cambios en la rama main
2. Ejecutar el despliegue automáticamente
3. Publicar la aplicación en la nube

---

# 🔐 11. Implementación de seguridad

Se creó el archivo:

```text id="9h4m2p"
staticwebapp.config.json
```

En el cual se configuraron encabezados HTTP como:

* Content-Security-Policy
* X-Frame-Options
* X-Content-Type-Options
* Strict-Transport-Security
* Referrer-Policy
* Permissions-Policy

Esto permitió mejorar la seguridad de la aplicación frente a ataques como XSS y clickjacking.

---

# ⚠️ 12. Problemas encontrados y soluciones

## 🔹 Problema 1: Restricción de región en Azure

**Error:**

```text id="5t6n2q"
RequestDisallowedByAzure
```

**Solución:**
Se cambió la región a:

```text id="7p8d3r"
East US 2
```

y se utilizó el plan:

```text id="8w2l6s"
Free
```

---

## 🔹 Problema 2: Estructura incorrecta del repositorio

Inicialmente el proyecto fue subido dentro de una carpeta adicional, lo cual impedía que Azure encontrara el archivo index.html.

**Solución:**
Se reorganizó el proyecto dejando los archivos en la raíz y se realizó un push forzado.

---

## 🔹 Problema 3: Bloqueo de API por políticas de seguridad

El encabezado Content-Security-Policy bloqueaba las peticiones hacia la API externa.

**Solución:**
Se permitió el dominio de PokéAPI mediante el uso de:

```text id="6v4k9y"
connect-src https://pokeapi.co
```

---

## 🔹 Problema 4: Error de carga de imágenes (404)

**Descripción:**
Las imágenes no cargaban correctamente y generaban errores 404 en el navegador.

**Causa:**
Las rutas definidas en el código no coincidían con la ubicación real de las imágenes dentro del proyecto.

**Solución:**
Se corrigieron las rutas de acceso a las imágenes para que coincidieran con la estructura real del proyecto, garantizando su correcta carga.

---

# 🔍 13. Validación de seguridad

Se utilizó la herramienta:

https://securityheaders.com/

Para verificar la implementación de encabezados de seguridad.

---

# 🌐 14. Resultado final

La aplicación quedó desplegada correctamente y accesible públicamente en la siguiente URL:

```text id="1y5k8q"
https://gentle-flower-09ed0ef0f.6.azurestaticapps.net/
```

---

# 🧠 Conclusión técnica

El proceso permitió aplicar conceptos fundamentales como:

* Construcción de aplicaciones Angular para producción
* Control de versiones con Git
* Integración continua (CI/CD)
* Configuración de servicios en la nube
* Implementación de políticas de seguridad HTTP

Se evidenció la importancia de mantener una estructura adecuada del proyecto y aplicar configuraciones de seguridad para garantizar un despliegue funcional y seguro.

---
