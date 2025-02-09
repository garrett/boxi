<img align="left" width="64" height="64" src="data/share/icons/hicolor/scalable/apps/dev.boxi.svg">

# Boxi

 - [GitHub Project Page](https://github.com/allisonkarlitskaya/boxi/)
 - [PyPI Project Page](https://pypi.org/project/boxi/)

A terminal emulator for use with Toolbox.

This is a thought-experiment app based around the idea of having a terminal emulator running in a separate container from the session inside of it, with the kernel as the only intermediary.

This is accomplished by means of file descriptor passing of the pseudo-terminal device from a small "agent" program running on the other side of a container boundary.  The agent is started using the usual container tools (`flatpak-spawn`, `toolbox`, `podman`), but creating a session is done purely via sockets.

Boxi can be installed via `pip`:

```
pip install boxi
```

and will soon be available on Flathub.

The install comes with a `.desktop` file, so Boxi can be launched from the desktop shell.  It can also be launched from the command line:

```
boxi
```

By default, Boxi will create sessions on the host system.  If you'd like to create sessions in a named Toolbox container, use `-c`:

```
boxi -c f36
```

Boxi uses different application identifiers when it is run for different containers.  This allows creating individual launcher icons for each container.  For example, `~/.local/share/applications/dev.boxi.f36.desktop`:

```
[Desktop Entry]
Type=Application
Name=Boxi (f36)
Icon=fedora
StartupNotify=true
Exec=boxi -c f36
```
