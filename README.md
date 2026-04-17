# OsPreferences

|方面|名称|链接|描述|
| -------------------------| -----------------------------| -----------------| -----------------|
|Font|`Ubuntu Mono`|[https://design.ubuntu.com/font](https://design.ubuntu.com/font)||
|Font|字魂正文宋楷|||
|Font|`OPPO Sans 4.0`|[https://www.coloros.com/article/A00000074](https://www.coloros.com/article/A00000074)||
|Gtk|`Andromeda`|[https://www.pling.com/p/2039961](https://www.pling.com/p/2039961)||
|Icons|`Azure Glassy Dark Icons`|[https://www.pling.com/p/2154036](https://www.pling.com/p/2154036)||
|Icons|`Elysia`|[https://www.pling.com/p/2167806](https://www.pling.com/p/2167806)|*cursor*|
|Python|`Poetry`|[https://python-poetry.org](https://python-poetry.org)||
|Terminal|`Murex`|[https://murex.rocks](https://murex.rocks)||
|Terminal|`Rio`|[https://github.com/raphamorim/rio](https://github.com/raphamorim/rio)||
|Terminal|`Contour`|[https://github.com/contour-terminal/contour](https://github.com/contour-terminal/contour)||
|Terminal|`G`|[https://github.com/equationzhao/g](https://github.com/equationzhao/g)||
|Terminal|`Lf`|[https://github.com/gokcehan/lf](https://github.com/gokcehan/lf)||

## Get start

```shell
ln -s ~/Lokalius/OsPreferences/profile ~/.profile
ln -s ~/Lokalius/OsPreferences/murex_profile ~/.murex_profile
ln -s ~/Lokalius/OsPreferences/config/g ~/.config/g
ln -s ~/Lokalius/OsPreferences/config/murex ~/.config/murex
ln -s ~/Lokalius/OsPreferences/config/pypoetry ~/.config/pypoetry
ln -s ~/Lokalius/OsPreferences/config/trae/settings.json ~/.config/Trae/User/settings.json
```

## About

### Rio

#### Q&A

- `ssh`连接退格异常：写`export TERM=xterm-256color`到`.bashrc`中

### Trae

#### Extension

|插件|链接|作者|描述|
| -------------------------| -----------------------------| -----------------| -----------------|
|`Kiro Theme`|[https://marketplace.visualstudio.com/items?itemName=MohdZaid.kiro-theme](https://marketplace.visualstudio.com/items?itemName=MohdZaid.kiro-theme)|`Mohd Zaid`||
|`Simple Icons`|[https://marketplace.visualstudio.com/items?itemName=Comdec.simple-icons](https://marketplace.visualstudio.com/items?itemName=Comdec.simple-icons)|`Comdec`||
|`Pylance`|[https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance)|`Microsoft`|`python` LSP|

#### VSIX Download in Browser

```javascript
(function gainVscVsix() {
  const scriptEle = document.querySelector('.jiContent');
  const { "Resources": { PublisherName, ExtensionName, Version } } = JSON.parse(scriptEle.textContent);
  const reap = `https://marketplace.visualstudio.com/_apis/public/gallery/publishers/${PublisherName}/vsextensions/${ExtensionName}/${Version}/vspackage`;
  console.info(reap);
})()
```
