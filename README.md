# WebEjemplo — EP1 DevOps

Proyecto mínimo (HTML estático) para evidenciar flujo DevOps: control de versiones, ramificación, PRs y CI con GitHub Actions.

## Tecnologías
- HTML estático
- Git + GitHub
- GitHub Actions (CI)

---

## Estrategia de ramas — **GitFlow**
- **main**: rama estable / “producción”. Solo recibe merges por PR.
- **develop**: integración de funcionalidades. Base de trabajo diaria.
- **feature/<nombre>**: nuevas funcionalidades; parten desde `develop` y vuelven a `develop` via PR.
- **hotfix/<nombre>**: correcciones urgentes que parten desde `main`. Se fusionan a `main` y luego se integran a `develop`.

**Justificación:** La pauta de la evaluación exige explícitamente `main`, `develop`, `feature/*` y `hotfix/*`. GitFlow modela exactamente ese flujo y facilita la colaboración con PRs, revisiones y trazabilidad.

---

## Convenciones de ramas y commits
**Ramas**
- `feature/<kebab-case>` (ej: `feature/mejora-logging`)
- `hotfix/<kebab-case>` (ej: `hotfix/corrige-titulo`)

**Commits (Convencional Commits “lite”)**
- `feat:` nueva funcionalidad  
- `fix:` corrección de bug  
- `docs:` documentación  
- `chore:` tareas menores (build, configs)  
- `refactor:` cambio interno sin alterar comportamiento  
- `test:` pruebas  

Ejemplo: `feat: agrega validación de formulario`

---

## Flujo de trabajo (PR/Merge)
1. Crear rama `feature/...` desde `develop`.
2. Commits pequeños y claros.
3. Abrir **Pull Request → develop**, asignar revisor, describir cambios y adjuntar evidencia (capturas si aplica).
4. Merge con **Squash** (historial limpio).
5. Para hotfix:
   - Crear `hotfix/...` desde `main`
   - PR → `main`
   - Una vez fusionado, **sincronizar `develop`** (merge o cherry-pick).

---

## CI — GitHub Actions
El workflow `CI` se ejecuta:
- en **push** a `develop`, y
- en **pull_request** hacia `main`.

Pasos mínimos:
- Checkout del repo
- Verificación básica (placeholder).  

> Este proyecto es estático; el pipeline valida solo que el flujo CI se dispare correctamente. (Se puede extender con linters o pruebas e2e si se requiere.)

---

## Estructura

📂 WebEjemplo  
 ├── 📄 index.html           # Página HTML estática principal  
 ├── 📄 README.md            # Documentación principal del proyecto  
 ├── 📄 CONTRIBUTING.md      # Guía para contribuir (pendiente de agregar)  
 ├── 📄 CHANGELOG.md         # Historial de cambios (pendiente de agregar)  
 └── 📂 .github/workflows/   # Configuración de CI con GitHub Actions  
     └── ci.yml

---

✍️ Autor: **Sergio Araya**  
📅 Proyecto académico — *Ingeniería en Informática, DUOC UC*
   Ramo: Ingeniería DEVOPS
