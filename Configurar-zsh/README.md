# Configuración del Entorno de Terminal: Zsh + Micro + Oh My Zsh! + Powerlevel10k

Guía paso a paso para configurar una terminal moderna, intuitiva y visualmente atractiva en **EndeavourOS / Arch Linux**, utilizando **Zsh** como shell predeterminado, **Micro** como editor de texto, **Oh My Zsh!** como framework de gestión y **Powerlevel10k** como tema visual principal.

---

## Prerrequisitos

Antes de comenzar, asegúrate de tener instalada la fuente **JetBrainsMono Nerd Font** para visualizar correctamente los iconos de Git y símbolos de la terminal:

```bash
sudo pacman -S ttf-jetbrains-mono-nerd
```
**Nota para VS Code:** Si usas Visual Studio Code, ve a Settings (Ctrl + ,), busca terminal.integrated.fontFamily y establece su valor en 'JetBrainsMono Nerd Font'.

## Paso 1: Instalar Zsh y Micro

1. Instalar los paquetes de los repositorios oficiales
```bash
sudo pacman -S zsh micro util-linux
```
2. Cambiar el shell predeterminado a zsh
```bash
chsh -s /usr/bin/zsh
```
*(Cierra la sesión y vuelve a entrar o reinicia para que el cambio de shell surta efecto).*

3.  (Cierra la sesión y vuelve a entrar o reinicia para que el cambio de shell surta efecto).
```bash
touch ~/.zshrc
```

## Paso 2: Instalar Oh My Zsh!
Ejecuta el script de instalación oficial de Oh My Zsh!:

```bash
sh -c "$(curl -fsSL [https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh](https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh))"
```
Si el instalador te pregunta si deseas cambiar el shell predeterminado a Zsh, confirma presionando `Y`.

## Paso 3: Instalar Plugins de Zsh (Autosugerencias y Resaltado)

Clona los complementos de autocompletado y resaltado de sintaxis dentro del directorio personalizado de Oh My Zsh:

```bash
git clone [https://github.com/zsh-users/zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions) ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

git clone [https://github.com/zsh-users/zsh-syntax-highlighting.git](https://github.com/zsh-users/zsh-syntax-highlighting.git) ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
## Paso 4: Instalar el Tema Powerlevel10k (p10k)
Clona el repositorio oficial de Powerlevel10k en la carpeta de temas de Oh My Zsh:
```bash 
git clone --depth=1 [https://github.com/romkatv/powerlevel10k.git](https://github.com/romkatv/powerlevel10k.git) ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```
## Paso 5: Configurar `~/.zshrc`

Abre tu archivo de configuración con Micro:

``` bash 
micro ~/.zshrc
```
Asegúrate de ajustar los siguientes puntos en tu archivo:

1. Definir el tema Powerlevel10k:
```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```
2. Activar los plugins instalados:
```bash 
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```
3. Establecer Micro como el editor por defecto del sistema:
Añade al final del archivo:
```bash
export EDITOR='micro'
export VISUAL='micro'
```
Guarda los cambios con `Ctrl + S` y sal del editor con `Ctrl + Q`.

## Paso 6: Aplicar Cambios y Configurar Powerlevel10k
Recarga la configuración de Zsh para iniciar el asistente de Powerlevel10k:
```bash
source ~/.zshrc
```
Si el asistente visual no inicia automáticamente, ejecútalo manualmente con:
```bash 
p10k configure
```
O intenta cerrando la terminal y abriendola de nuevo.

Sigue las instrucciones en pantalla para elegir el estilo visual, los iconos, el reloj y los separadores que prefieras.

## Verificación Final

Para confirmar que todo está configurado correctamente, ejecuta:
```bash 
echo $SHELL && echo$EDITOR
```

- La primera línea debe devolver /usr/bin/zsh o /bin/zsh.

- La segunda línea debe devolver micro.

- Los comandos válidos deben aparecer en verde y los inválidos en rojo.

