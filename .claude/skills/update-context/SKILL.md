---
name: update-context
description: Audita el proyecto y actualiza context/context_backend.md y context/context_frontend.md para que reflejen el estado real del código (no lo que se supone que debería existir).
---

## Qué hacer

Este comando sincroniza `/context` con la realidad del repo. Úsalo cuando se sospeche
que el contexto quedó desactualizado (varios cambios seguidos, edición manual fuera de
Claude, retomar el proyecto después de un tiempo, etc.).

1. **Revisa el estado real del proyecto**, no documentación vieja:
   - `git status` y `git diff` para ver qué cambió.
   - Estructura real de `backend/` (migraciones en `database/migrations/`, modelos en
     `app/Models/`, rutas en `routes/api.php`, versión de Laravel/PHP en `composer.json`).
   - Estructura real de `frontend/` (componentes en `src/components/`, páginas en
     `src/pages/`, servicios en `src/services/`, versión de React/Vite/TS en `package.json`).
   - Estado de la base de datos si aplica (tablas existentes vs. las que dice el contexto).

2. **Lee** `context/context_backend.md` y `context/context_frontend.md` actuales.

3. **Compara** lo documentado contra lo real. Identifica:
   - Cosas que el contexto dice que existen pero no existen.
   - Cosas que ya existen en el código pero no están en el contexto.
   - Decisiones o fases marcadas como pendientes que ya se completaron (o viceversa).

4. **Actualiza ambos archivos** para que coincidan con la realidad actual:
   - `context_backend.md`: stack y versiones reales, estado de la BD/migraciones,
     endpoints que existen de verdad, decisiones tomadas.
   - `context_frontend.md`: stack y versiones reales, estructura de componentes/páginas/
     servicios que existen de verdad, estado de testing (Jest/RTL configurado o no).
   - Referencia el avance en `/plan` (qué fases/pasos están `(listo)`).

5. **No inventes nada** que no hayas verificado leyendo el código o corriendo comandos
   de solo lectura (`git status`, `ls`, `cat`, `php artisan route:list`, etc.). Si algo
   no está claro, pregunta antes de asumir.

6. Al terminar, da un resumen breve de qué se corrigió o agregó en cada archivo de
   contexto (no hace falta repetir todo el contenido).
