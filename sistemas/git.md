# Configuracion de acceso por SSH

```bash
# Crear una clave SSH
ssh-keygen -t ed25519

# Iniciar Agente SSH 
eval "$(ssh-agent -s)"` `ssh-add ~/.ssh/id_ed25519

# Mostrar tu clave pública
cat ~/.ssh/id_ed25519.pub
```

>Copia el output `ssh-ed25519 AAAAC3... tu_email@example.com`

>En GitHub Settings → SSH and GPG keys → New SSH key → Pega la clave pública y guarda.

```bash
# Comprobar la conexión
ssh -T git@github.com

# Usar SSH en tu repositorio
git clone git@github.com:USUARIO/REPOSITORIO
git remote set-url origin git@github.com:USUARIO/REPOSITORIO

# Comprueba
git remote -v
```

# Git: Comandos
## Descargas

```bash
# Empezar un repo 
git init

# Clonar el repo 
git clone http:///myrepo.com

# Actualizar mi repo 
git pull
```

## Flujo de Trabajo

```bash
# Ver el estado del repo 
git status

# Agregar al area de trabajo 
git add .

# Hacer un commit 
git commit -m "my message"

# Ver la lista de commits 
git commit log

# Crear una nueva rama 
git checkout -b rama

# Cambiar a una rama existente 
git switch rama

# Eliminar una rama 
git branch -d rama`

# Subir al repositorio (pull request) 
git push -u repo rama

# Subir al repositorio main 
git push
```


