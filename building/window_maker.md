## Window Maker as a low resource window manager
My laptop is too old to run Unity and I decided to switch to Window Maker.

## Configuration
* Useful [resource](https://administratosphere.wordpress.com/2011/07/16/configuring-a-windowmaker-desktop-in-ubuntu/)
* Remember to configure autostart and set it to be executable.
* For browser, use midori (0.5.11). Very fast. Minimal RAM.
* Use guake as a drop down terminal. Autostar at login. Use F12 to bring up a terminal.

## Tip
* If window title bar is outside the screen. Do the following
  - Click middle button (or left + right button) to bring up window list.
  - Select the one that is outside the screen.
  - Ctrl+Esc to bring up a menu which could be outside the screen as well. Use down arrow until the menu shows up.
  - Choose Resize/Move. Use arrow key to move and ctrl + arrow to resize.
* Set default browser: `sudo update-alternatives --config x-www-browser` 
  and choose midori
  This will register `x-www-browser` with midori.
* Set default browser for jupyter
   - `sudo update-alternatives --config x-www-browser`
   - Edit `.jupyter/jupyter_notebook_config.py`:
   ```python
   c.NotebookApp.browser = 'x-www-browser'
   ```
   jupyter uses a python module `webbrowser` to open a browser. Use the following to check which are registered.
   ```python
   import webbrowser
   print webbrowser._browsers
   ```
