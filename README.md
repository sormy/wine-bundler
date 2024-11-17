WINE BUNDLER
============

About
-----

Wine bundler - simple command line alternative to wine bottler and wineskin to convert windows applications into macOS application bundles.

This simple bash script will let you easily wrap existing wine prefix into bundle that could be used to launch application or for standalone distribution.

Inspired by non-working by default GoG's "Divine Divinity" wine application bundle.

https://www.artembutusov.com/how-to-wrap-wine-applications-into-macos-x-application-bundle/

Features
--------

- creates macOS application bundle
- list available wine versions
- download specific wine version
- cache downloaded wine binaries locally
- install prefix
- customizable bundle name
- customizable bundle icon
- customizable launcher + menu
- auto convert png to icns bundle icon
- auto convert GoG's ico's to icns bundle icon
- simaple bash script that you could easily tune for your needs

While this script doesn't provide bundle update feature yet you could still manually fix bundle configuration as you want after bundle creation.

Installation
------------

Install optional dependency `ImageMagick`:

```shell
brew install imagemagick
```

Install `wine-bundler`:

```shell
wget https://raw.githubusercontent.com/sormy/wine-bundler/master/wine-bundler \
  -O /usr/local/bin/wine-bundler
chmod +x /usr/local/bin/wine-bundler
```

Show `wine-bundler` help screen:

```shell
wine-bundler -h
```

Example
-------

Assuming that you already had created wine prefix, installed game, tuned with winetricks etc.

Divine Divinity example with menu:

```shell
wine-bundler \
  -i ~/.wine/drive_c/GOG\ Games/Divine\ Divinity\ \(Russian\)/gfw_high.ico \
  -n "Divine Divinity" \
  -c ru_RU.UTF-8 \
  -w stable \
  -a win32 \
  -p ~/.wine \
  -m 'Divine Divinity=c:\GOG Games\Divine Divinity (Russian)\div.exe' \
  -m 'Settings=c:\GOG Games\Divine Divinity (Russian)\configtool.exe'
```

Divine Divinity example without menu:

```shell
wine-bundler \
  -i ~/.wine/drive_c/GOG\ Games/Divine\ Divinity\ \(Russian\)/gfw_high.ico \
  -n "Divine Divinity" \
  -c ru_RU.UTF-8 \
  -w stable \
  -a win32 \
  -p ~/.wine \
  -s 'c:\GOG Games\Divine Divinity (Russian)\div.exe'
```

Earth 2150 Trilogy example with menu:

```shell
wine-bundler \
  -i ~/.wine/drive_c/GOG\ Games/Earth\ 2150/goggame-1207661853.ico \
  -n "Earth 2150" \
  -c ru_RU.UTF-8 \
  -w stable \
  -a win32 \
  -p ~/.wine \
  -m 'Earth 2150: Escape from the Blue Planet=c:\GOG Games\Earth 2150\Earth2150.exe' \
  -m 'Earth 2150: Escape from the Blue Planet (Settings)=c:\GOG Games\Earth 2150\Setup.exe' \
  -m 'Earth 2150: The Moon Project=c:\GOG Games\Earth 2150 - The Moon Project\TheMoonProject.exe' \
  -m 'Earth 2150: The Moon Project (Settings)=c:\GOG Games\Earth 2150 - The Moon Project\Setup.exe' \
  -m 'Earth 2150: Lost Souls=c:\GOG Games\Earth 2150 - Lost Souls\LostSouls.exe' \
  -m 'Earth 2150: Lost Souls (Settings)=c:\GOG Games\Earth 2150 - Lost Souls\Setup.exe'
```

Bundle will be produced in current working directory.

Dependencies
------------

This script should work on both Linux and macOS but some functionality is available only on macOS, for example, utilities `iconutil` and `sips` are available only on macOS.

This script is also using installed `ImageMagic` for image conversion to `icns` format that should be used for macOS application bundles.

License
-------

MIT
