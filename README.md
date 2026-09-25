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

在 `registry.json` 的 `plugins` 数组里追加一条。`repository` 必须是 `https://github.com/所有者/仓库`。安装时 CLIProxyAPI 会读取该仓库的最新 Release。

Release 需要包含当前平台的压缩包和 `checksums.txt`：

```text
<插件ID>_<版本>_<系统>_<架构>.zip
checksums.txt
```

压缩包根目录直接放动态库，例如 `my-plugin.so`，不要放进子目录。`checksums.txt` 使用 sha256：

```text
<sha256>  my-plugin_1.0.0_linux_amd64.zip
```
