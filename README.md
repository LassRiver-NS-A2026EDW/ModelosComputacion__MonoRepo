
# 🏢 Modelos de Computación - Monorepo

![GitHub](https://img.shields.io/badge/monorepo-submodules-blue)
![Angular](https://img.shields.io/badge/Angular-DD0031?style=flat&logo=angular&logoColor=white)
![Django](https://img.shields.io/badge/Django-092E20?style=flat&logo=django&logoColor=white)

Monorepo que orquesta los proyectos de **Angular** (frontend) y **Django** (backend) usando **submódulos de Git**.

---

## 📁 Estructura

```
ModelosComputacion__MonoRepo/
├── angular/          → 🖥️ Frontend (Angular)
│   └── (apunta a github.com:LassRiver-NS-A2026EDW/ModelosComputacion__AngularFrontend)
├── django/           → ⚙️ Backend (Django + Docker)
│   └── (apunta a github.com:LassRiver-NS-A2026EDW/ModelosComputacion_DjangoBackend)
├── .gitmodules       → Configuración de los submódulos
└── README.md         → Este archivo
```

Cada subcarpeta (`angular/` y `django/`) **NO** contiene el código directamente, sino que son **referencias (submódulos)** a sus repositorios individuales en GitHub.

---

## 🚀 Primer clonado (la primera vez)

Hay **dos formas** de clonar el proyecto. Elige la que más te guste:

### Opción 1: Clonar y luego inicializar submódulos

```bash
git clone git@github.com:LassRiver-NS-A2026EDW/ModelosComputacion__MonoRepo.git
cd ModelosComputacion__MonoRepo
git submodule update --init --recursive
```

### Opción 2: Clonar con submódulos incluidos (recomendado ☝️🤓)

```bash
git clone --recurse-submodules git@github.com:LassRiver-NS-A2026EDW/ModelosComputacion__MonoRepo.git
cd ModelosComputacion__MonoRepo
```

---

## 🔄 Flujo de trabajo diario

### 1. Trabajar en un submódulo (ej: `angular/`)

```bash
cd angular                # Entrar al submódulo
git checkout main         # Asegurarte de estar en main
# ... haces tus cambios mágicos ...
git add .
git commit -m "feat: mi cambio épico"
git push origin main       # Subes los cambios al repo de Angular
cd ..                     # Volver al monorepo
```

### 2. Actualizar la referencia en el monorepo

Después de pushear cambios en un submódulo, el monorepo sigue apuntando al **commit anterior**. Hay que actualizarlo:

```bash
git add angular            # Registrar el nuevo commit del submódulo
git commit -m "chore: update angular submodule"
git push                   # Subir al monorepo
```

### 3. Traer los últimos cambios de los submódulos

Cuando alguien más haya actualizado los submódulos, o cuando vuelvas después de un tiempo:

```bash
git pull                    # Traer cambios del monorepo
git submodule update --remote   # Actualizar submódulos al último commit de sus remotos
```

O si quieres ver primero qué cambió:

```bash
git pull
git submodule update --remote --init --recursive
```

### 4. Ver en qué commit está cada submódulo

```bash
git submodule status
```

Ejemplo de salida:
```
 7e021e3f5f8a9b1c2d3e4f5a6b7c8d9e0f1a2b3c angular (v1.0.0)
 18b5dea1234567890abcdef1234567890abcdef12 django (v2.1.0)
```

---

## ⚠️ Cosas que te van a doler (para que no sufras solo)

1. **Olvidar hacer `git submodule update --init --recursive`** después de clonar → las carpetas `angular/` y `django/` aparecen vacías. No te asustesss, solo ejecuta ese comando y ya.

2. **Hacer cambios dentro de un submódulo y olvidar pushearlos** → haces `git push` en el monorepo, subes la referencia al nuevo commit, pero el repo del submódulo no se actualiza. Cuando otro clone, intentará bajar un commit que no existe en el remoto del submódulo. SOLUCIÓN: siempre pushea el submódulo PRIMERO, y después el monorepo.

3. **Hacer `git add .` en el monorepo y commitear sin querer cambios del submódulo** → no pasa nada grave, pero commit eas el cambio de referencia. Es normal, solo ponle un mensaje como `"chore: update submodules"`.

4. **Si ves `dirty` en `git submodule status`** → significa que tocaste archivos dentro del submódulo sin commitearlos. Puedes hacer `git submodule update --force` para descartar cambios locales (CUIDADO: borra cambios no commiteados).

---

## 🧹 Comandos útiles para tu masoquismo

```bash
# Actualizar TODOS los submódulos a su último commit en main
git submodule foreach git checkout main
git submodule foreach git pull origin main

# Si todo se rompió y queres empezar de cero los submódulos
git submodule deinit -f .
git submodule update --init --recursive

# Ver diferencias incluyendo submódulos
git diff --submodule

# Hacer push de TODO (monorepo + submódulos) de una
git push --recurse-submodules=on-demand
```

---

## 🐳 Quick start (Django con Docker)

```bash
cd django
docker compose up --build
```

Para más detalles de cada proyecto, revisa sus README individuales:

- [README de Angular](./angular/README.md)
- [README de Django](./django/README.md)

---

> "El que usa submódulos sin leer el README, va a terminar llorando en producción." — Sábias palabras de un desarrollador experimentado. O masoquista.
