# CPA 插件商店

这是一个独立的 [CLIProxyAPI](https://github.com/router-for-me/CLIProxyAPI) 插件商店源。清单在 `registry.json`，以后新增插件只改这个文件，不必再为每个插件单独准备一个商店地址。

商店地址：

```text
https://raw.githubusercontent.com/moxi000/cpa-plugin-store/main/registry.json
```

在 `config.yaml` 中追加：

```yaml
plugins:
  enabled: true
  store-sources:
    - "https://raw.githubusercontent.com/moxi000/cpa-plugin-store/main/registry.json"
```

保存后，管理面板的插件商店里会出现这个源，以及其中列出的插件。

## 当前插件

| 插件 | ID | 代码仓库 |
| --- | --- | --- |
| 模型目录覆写 | `models-cache-override` | https://github.com/moxi000/models-cache-override |

## 加入新插件

清单格式与 [插件商店发布格式](https://help.router-for.me/cn/plugin/development.html#%E6%8F%92%E4%BB%B6%E5%95%86%E5%BA%97%E5%8F%91%E5%B8%83%E6%A0%BC%E5%BC%8F) 一致。`schema_version` 必须是 `1`。每条插件的 `id`、`name`、`description`、`author`、`repository` 必填，`repository` 必须是 `https://github.com/{owner}/{repo}`。`version` 只是展示兜底；实际安装版本来自该仓库最新 Release 的 tag，tag 可以带前导 `v`。

在 `plugins` 数组里追加一条后，到插件仓库发布 Release。资产名称：

```text
<pluginID>_<version>_<goos>_<goarch>.zip
checksums.txt
```

压缩包根目录必须直接包含动态库，例如 `my-plugin.so`，不能放在子目录里。`checksums.txt` 为 sha256：

```text
<sha256>  my-plugin_1.0.1_linux_amd64.zip
```
