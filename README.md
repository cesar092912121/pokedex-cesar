# 📘 PokeDex - Despliegue en la Nube

## 📌 Descripción

Aplicación web tipo PokeDex desplegada en la nube mediante Azure Static Web Apps, consumiendo datos desde la API pública PokéAPI.

---

## 👨‍💻 Integrante

* Cesar Jimenez Ferrer

---

# ☁️ 1. Creación de cuenta en Azure for Students

Se utilizó Azure for Students para el despliegue del proyecto.

### 🔹 Proceso:

1. Se ingresó a la plataforma de Azure.
2. Se inició sesión con el correo institucional.
3. Se activó la suscripción Azure for Students.
4. Azure validó automáticamente la cuenta académica.
5. Se habilitó el acceso a recursos gratuitos en la nube.

---

# 📂 2. Clonación del repositorio

```bash
git clone https://github.com/rcuello/ac4dem1a.git
cd ac4dem1a
```

---

# ⚙️ 3. Construcción del proyecto

```bash
cd sistemas-distribuidos/poke-dex-lab/source/pokedex-angular
npm install
npx ng build
```

---

# 📦 4. Preparación del despliegue

```bash
cd dist/pokedex-angular
```

---

# 🚀 5. Subida a GitHub

```bash
rm -rf .git
git init
git remote add origin https://github.com/cesar092912121/pokedex-cesar.git
git add .
git commit -m "deploy pokedex"
git branch -M main
git push --set-upstream origin main --force
```

---

# ☁️ 6. Despliegue en Azure

* Servicio: Static Web Apps
* SKU: Free
* Región: East US 2
* Repositorio: pokedex-cesar
* Rama: main

Configuración:

```
App location: /
Output location: /
```

---

# 🔐 7. Seguridad

Se implementaron encabezados HTTP mediante el archivo:

```
staticwebapp.config.json
```

---

# 🌐 8. URL pública

La aplicación quedó disponible en:

```
https://gentle-flower-09ed0ef0f.6.azurestaticapps.net/
```

---

# 🧠 Conclusión

Se logró desplegar correctamente la aplicación en la nube aplicando buenas prácticas de seguridad, control de versiones y automatización de despliegue.
