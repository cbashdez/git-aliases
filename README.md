# 🔧 Mis Aliases de Git

Referencia personal de aliases configurados globalmente en Git.  
Para aplicar un alias en una máquina nueva, copia el comando y ejecútalo en la terminal.

---

## 📊 Log y Estado

### `git lg` — Log visual con colores y ramas
```bash
git config --global alias.lg "log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"
```
Muestra el historial de commits con gráfico de ramas en ASCII, hash corto, tiempo relativo, mensaje y autor, todo con colores.

---

### `git s` — Status corto
```bash
git config --global alias.s "status --short"
```
Versión compacta de `git status`. Muestra los archivos modificados en una línea por archivo en vez del mensaje largo.

---

## ➕ Staging y Commits

### `git cm` — Commit con mensaje directo
```bash
git config --global alias.cm "commit -m"
```
Hace un commit pasando el mensaje directamente sin abrir el editor.  
Uso: `git cm "mi mensaje"`

---

### `git ac` — Add all + Commit en un solo paso
```bash
git config --global alias.ac "!git add -A && git commit -m"
```
Agrega todos los archivos modificados al staging y hace el commit en un solo comando.  
Uso: `git ac "mi mensaje"`

---

### `git amend` — Editar el último commit
```bash
git config --global alias.amend "commit --amend"
```
Permite modificar el mensaje o agregar archivos al commit más reciente (antes de hacer push). Abre el editor con el mensaje anterior para que lo edites.

---

### `git amendf` — Añadir al último commit sin cambiar el mensaje
```bash
git config --global alias.amendf "commit --amend --no-edit"
```
Agrega los archivos que tengas en staging al último commit sin tocar el mensaje. Útil cuando olvidaste incluir un archivo.

---

## 🌿 Ramas

### `git b` — Listar ramas locales
```bash
git config --global alias.b "branch"
```
Lista todas las ramas locales del repositorio. La rama actual aparece marcada con `*`.

---

### `git ba` — Listar todas las ramas (locales y remotas)
```bash
git config --global alias.ba "branch -a"
```
Lista las ramas locales y también las remotas (las que están en GitHub/GitLab, etc.).

---

### `git cob` — Crear rama y cambiarse a ella
```bash
git config --global alias.cob "checkout -b"
```
Crea una rama nueva y cambia a ella en un solo comando.  
Uso: `git cob feature/login`

---

### `git del` — Eliminar rama local
```bash
git config --global alias.del "branch -d"
```
Elimina una rama local que ya fue mergeada. Git no te deja borrarla si tiene cambios sin mergear (para eso existe `-D`).  
Uso: `git del feature/login`

---

## ↩️ Deshacer Cambios

### `git unstage` — Sacar archivo del staging
```bash
git config --global alias.unstage "restore --staged"
```
Quita un archivo del staging area sin borrar los cambios. Es el opuesto de `git add`.  
Uso: `git unstage index.html`

---

### `git undo` — Deshacer el último commit (sin perder los cambios)
```bash
git config --global alias.undo "reset HEAD~1 --mixed"
```
Deshace el último commit y devuelve los archivos al estado de "modificados pero sin commitear". El código no se pierde, solo el commit.

---

### `git undohard` — Deshacer el último commit (borrando todo) ⚠️
```bash
git config --global alias.undohard "reset HEAD~1 --hard"
```
Deshace el último commit y borra todos los cambios para siempre. Úsalo con cuidado, no hay manera de recuperar lo perdido.

---

## 📦 Stash

### `git save` — Guardar cambios en el stash con nombre
```bash
git config --global alias.save "stash push -m"
```
Guarda los cambios actuales en el stash con una descripción para identificarlos después.  
Uso: `git save "trabajo en progreso del login"`

---

### `git pop` — Recuperar el último stash
```bash
git config --global alias.pop "stash pop"
```
Recupera los cambios del último stash guardado y lo elimina de la lista de stashes.

---

### `git sl` — Ver lista de stashes
```bash
git config --global alias.sl "stash list"
```
Muestra todos los stashes guardados con su índice y descripción.

---

## 🌐 Remoto

### `git p` — Push al remoto
```bash
git config --global alias.p "push"
```
Sube los commits al repositorio remoto (GitHub, etc.).  
Uso: `git p origin main`

---

### `git pl` — Pull del remoto
```bash
git config --global alias.pl "pull"
```
Descarga y aplica los cambios del repositorio remoto en tu rama actual.

---

### `git pf` — Push forzado (seguro)
```bash
git config --global alias.pf "push --force-with-lease"
```
Hace un push forzado pero de forma segura: solo lo permite si nadie más ha subido cambios después de tu último pull. Úsalo después de un `amend` o `rebase`. Más seguro que `--force`.
