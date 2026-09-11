# 🧮 Calculadora en Python — Práctica de Git Avanzado

Proyecto simple de calculadora con operaciones básicas, usado 
para practicar comandos avanzados de Git.

## ⚙️ Funcionalidades
- Sumar
- Restar
- Multiplicar
- Dividir

## 📝 Cómo ejecutar
```
python calculadora.py
```

---

## 📚 Teoría — Comandos que vas a usar

### git commit --amend
Modifica el ÚLTIMO commit que hiciste (cambia su mensaje y/o 
agrega archivos que olvidaste). No crea un commit nuevo, corrige 
el anterior.
```
git commit --amend -m "nuevo mensaje"
```

### git reset
Deshace commits. `HEAD~1` significa "un commit atrás del actual" 
(`HEAD~2` serían dos atrás, etc.)

Tiene 3 tipos:
- `--soft`: deshace el commit, pero tus cambios siguen listos 
  para volver a commitear
- `--mixed` (el que se usa si no escribes nada): deshace el 
  commit y el "add", los cambios quedan en tus archivos sin preparar
- `--hard`: borra TODO, incluso los cambios en tus archivos 
  (¡cuidado, esto no se puede deshacer!)

```
git reset --soft HEAD~1
```

---

## 🎯 Tu tarea

### Paso 1 — Configurar tu identidad
```
git config user.name "Tu Nombre"
git config user.email "tu-correo"
```

### Paso 2 — Explorar el historial
```
git log --oneline
```
Verás algo como:
```
a1b2c3d agrego cosas
cbf1618 arreglo
fd78525 agrego funcion
e6375a2 primer commit
```

### Paso 3 — Corregir el ÚLTIMO commit con amend
El mensaje "agrego cosas" no sigue el formato de conventional 
commits. Corrígelo:
```
git commit --amend -m "docs: agregar instrucciones del proyecto"
```
Verifica con `git log --oneline` — el mensaje del último commit 
ya cambió.

### Paso 4 — Practicar reset
Deshaz el commit que acabas de corregir, usando `--soft`:
```
git reset --soft HEAD~1
```
Ejecuta `git log --oneline` — notarás que ese commit YA NO 
aparece. Ejecuta `git status` — verás que los cambios siguen 
ahí, listos para commitear de nuevo:
```
git commit -m "docs: agregar instrucciones del proyecto"
```

### Paso 5 — Nuevos commits (conventional commits)
Agrega al menos 2 mejoras al proyecto. Escribe TÚ MISMO el 
mensaje, siguiendo el formato:
- `feat:` para funcionalidad nueva
- `docs:` para cambios en documentación
- `fix:` para corregir un error

### Paso 6 — Subir a tu repositorio
```
git push -u origin main
```
### Investigación adicional
Ejecuta git reflog. En tu README.md, en una sección 
"Investigación adicional", explica en 2-3 líneas qué información 
muestra este comando.

## ✅ Entrega
Link de tu repositorio (fork) + pantallazo de "git log --oneline"

## 📚 Teoría — Actividad 2

## ¿Qué es Semantic Versioning (SemVer)?

**Semantic Versioning** (o *Versionado Semántico*) es un estándar y conjunto de reglas que define cómo asignar y mantener los números de versión en un proyecto de software. Su objetivo principal es comunicar de forma clara a los usuarios y desarrolladores qué tipo de cambios incluye una nueva actualización (si incluye cambios drásticos, nuevas funcionalidades o solo corrección de errores).

El formato estándar consta de tres números separados por puntos: **`MAJOR.MINOR.PATCH`** (ejemplo: `v1.0.0`).

---

### Estructura y Ejemplos de SemVer

#### 1. MAJOR (Versión Mayor) — `X.0.0`
* **¿Cuándo cambia?** Cuando se realizan cambios drásticos en la arquitectura o en la API que **rompen la compatibilidad con versiones anteriores** (*Breaking Changes*). Los usuarios deben modificar su código o configuración para actualizar a esta versión.
* **Ejemplo:** Pasa de `v1.5.2` a **`v2.0.0`**.
  * *Caso real:* Una aplicación cambia completamente su base de datos o elimina endpoints antiguos de una API REST.

#### 2. MINOR (Versión Menor) — `1.X.0`
* **¿Cuándo cambia?** Cuando se añaden **nuevas funcionalidades de manera retrocompatible** (sin romper nada de lo que ya funcionaba).
* **Ejemplo:** Pasa de `v1.2.1` a **`v1.3.0`**.
  * *Caso real:* Se añade un nuevo botón de "Modo Oscuro" o se integra una nueva pasarela de pago sin alterar el funcionamiento existente.

#### 3. PATCH (Parche / Corrección) — `1.0.X`
* **¿Cuándo cambia?** Cuando se aplican **correcciones de errores (bugs)**, parches de seguridad o pequeñas optimizaciones internas que no añaden funcionalidades ni rompen compatibilidad.
* **Ejemplo:** Pasa de `v1.0.0` a **`v1.0.1`**.
  * *Caso real:* Se corrige un error tipográfico en un formulario o se arregla un fallo donde un botón no respondía al hacer clic.