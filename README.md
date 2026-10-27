# DeepSeek Harness 直播助手

一只住在 OBS 右下角的小鲸鱼：**读你的 B 站弹幕，按人格思考，冒泡回复，还能念出来。**

> 基于 DeepSeek Harness（DSH）+ RVC 音色转换，全程本地运行，弹幕只读不登录。

## 功能

- **弹幕自动回复**：弹幕进来 → 模型思考 → 气泡 + 语音同时出现，无需手动操作
- **会说话**：Edge TTS 底嗓 + 本地 RVC 换音色，1~18 字的短句，像真人在打字
- **谢礼物**：有人送礼立刻道谢，格式固定、后半句即兴
- **冷场自救**：安静 90 秒没人说话，自己冒一句碎碎念；下播自动闭嘴
- **可选「看屏幕」**：定期看一眼游戏画面，知道你在打什么、打到哪（默认关闭）

## 下载

👉 **[点这里下载最新版](https://github.com/SuperYuanji/zishe/releases/latest)**

## 安装（4 步）

1. **解压**到固定目录（别放下载文件夹），例如 `D:\whale`
2. **运行 `install.ps1`**（右键 → 使用 PowerShell 运行），填两个东西：
   - RVC 根目录（含 `runtime\`、`infer\` 的那层）
   - 你的 B 站直播间号
3. **让 DSH 装插件**：在 DSH 对话框里说
   > 用 plugin_manager 安装 `D:\whale\whale-live` 这个 bundle

   装完**完全退出 DSH 再打开**
4. **起服务 + OBS**：
   - 双击 `whale-tts\start-all.bat`（两个窗口）
   - 双击 `whale-obs-overlay\start.bat`（一个窗口）
   - OBS → 来源 → 浏览器 → URL `http://127.0.0.1:8765/`
   - **勾选「通过 OBS 控制音频」**（不勾没声音）

详细图文步骤见包内 **`TUTORIAL.md`**。

## 需要什么

| 依赖 | 说明 |
|---|---|
| Windows 10/11 | — |
| DeepSeek Harness 桌面版 | 提供插件机制与模型额度 |
| OBS Studio | 显示挂件 |
| RVC WebUI（7~9 GB） | 语音换音色，**包内不含**；没有也能用，把 `ttsEnabled` 设为 `false` |

## 常见问题

- **有气泡没声音**：OBS 源属性里没勾「通过 OBS 控制音频」，或 4892/4893 服务没起
- **弹幕不回复**：看 `%USERPROFILE%\.dsh\whale-live.status.json` 里的 `lastError`；`-352` 是 B 站风控，等十几分钟
- **`.bat` 闪退**：检查 `whale-tts\rvc-path.txt` 里的路径是否正确
- **端口被占用**：说明服务已经在跑，直接用，不要重复启动

## 版权与免责

- 代码：MIT
- 音色模型：**仅供学习交流，不随代码授权**，请勿二次分发或商用
- 角色图：来自开源项目 `dsh-whale-widget`，其美术素材不在 MIT 范围内
- 语音：Edge TTS 公开接口（非官方，可能失效）+ 本地 RVC
- 弹幕：仅匿名只读，不会登录或替你在直播间发言
