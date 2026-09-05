# Chuleta de Git y GitHub

Resumen de los comandos y conceptos aprendidos en este proyecto.

## Configuración (una sola vez)

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu-correo@ejemplo.com"
git config --global core.editor "code --wait"   # VS Code como editor
git config --global core.pager "cat"            # sin paginador en git log
```

## El ciclo diario

```bash
git status          # ¿cómo está todo? (gratis, úsalo siempre)
git diff            # ¿qué cambió exactamente?
git add <archivo>   # poner en escena
git commit -m "..." # grabar con descripción
git log --oneline   # historial compacto
```

**Regla de oro:** `git status` y `git log` son gratis. Úsalos antes y después de cada comando.

## Deshacer sin miedo

| Situación | Comando | ¿Toca historial? |
|-----------|---------|------------------|
| Cambio sin `add` | `git restore <archivo>` | No |
| Cambio con `add`, sin commit | `git reset` + `git restore <archivo>` | No |
| Cambio ya commiteado | `git revert HEAD` | Sí (agrega commit que anula) |
| Corregir último commit | `git commit --amend -m "..."` | Reescribe el último |

- `git revert HEAD --no-edit` → revierte sin abrir editor.
- Si te atrapa el paginador de `git log` (pantalla con `:` al final): pulsa `q`.

## Ramas

```bash
git branch               # ver ramas (* = en la que estás)
git switch -c <rama>     # crear rama y cambiarse (un paso)
git switch <rama>        # cambiarse
git merge <rama>         # fusionar esa rama hacia la actual
git branch -d <rama>     # borrar rama ya fusionada
```

**Conflicto** = dos ramas cambiaron la misma línea. Se resuelve así:
1. Editar el archivo, borrar los marcadores `<<<<<<<`, `=======`, `>>>>>>>`.
2. `git add <archivo>`
3. `git commit -m "Resuelvo conflicto: ..."`

Ver la "Y" de la fusión: `git log --oneline --graph --all`

**Ojo:** si solo una rama avanzó, Git hace *fast-forward* (adelanta el puntero) sin conflicto. El conflicto requiere que **ambas** ramas se hayan movido.

## GitHub (la nube)

```bash
git remote add origin <url>   # conectar con el repo remoto
git remote -v                 # ver la conexión
git push -u origin main       # subir rama y vincularla (-u solo la 1ª vez)
git push                      # subir cambios (ya vinculada)
git pull                      # bajar cambios de la nube
```

**Autenticación:** GitHub ya no acepta contraseña en terminal. Git Credential Manager abre una ventana del navegador (código de 8 dígitos) y recuerda tu sesión.

## Pull Request (flujo de equipo)

1. `git switch -c feature/x` → trabajar → `add` + `commit`
2. `git push -u origin feature/x`
3. En la web: **Compare & pull request** → revisar → **Create pull request**
4. **Merge pull request** → **Delete branch**
5. De vuelta en local: `git switch main` → `git pull`

## Limpieza y secretos

```bash
git branch -d <rama>                 # borrar rama local fusionada
git remote prune origin              # limpiar referencias remotas fantasmas
```

**Secretos (tokens, contraseñas, claves):**
- Nunca commitees un archivo con secretos (ej. `token.txt`).
- Bloquéalos en `.gitignore`:

```gitignore
# Secretos
token.txt
*.token
```

**Concepto clave:** `git branch -a` NO consulta la nube; muestra la última foto guardada en local. Si una rama remota ya no existe pero sigue apareciendo, límpiala con `git remote prune origin`.
