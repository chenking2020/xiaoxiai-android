# 离线AI宝（xiaoxiai-android）

一款**全程离线**的 Android 端侧 AI 助手：语音识别、机器翻译、语音合成与大语言模型全部跑在手机上，
音视频、文本与生成结果都不出设备、不联网。

- 语言：Kotlin + Jetpack Compose（Material 3）
- 最低系统：Android 8.0（API 26），目标 / 编译 SDK：API 36
- 推理：ONNX Runtime Android 1.26（主力）+ PyTorch Mobile Lite 2.1（辅助）+ OpenCV 4.9（扫描增强）

## 一、功能特性

<p align="center">
  <img src="images/APP%E9%A6%96%E9%A1%B5.jpg" width="240" alt="APP 首页">
</p>

首页按能力分卡片进入各智能体，右上角进入设置（主题、NPU 加速）。全程无登录、无联网，所有推理都在本机完成。

下列 **8 个智能体均已上线**。

### 1. 文本对话

以文字直接提问的端侧大模型问答。支持「深度思考 / 不思考」两种模式：不思考直接出正文、响应更快；深度思考先展开推理链（界面实时可见、思考过程可折叠）再作答，适合推理与复杂问题。可上传 txt / Word / PDF / 图片，提问时自动从文档里检索相关段落作答。回复按 Markdown 渲染（标题、列表、代码块、表格等），会话自动保存在本机，可随时从「历史」回看并继续追问。

<p align="center">
  <img src="images/%E6%96%87%E6%9C%AC%E5%AF%B9%E8%AF%9D.jpg" width="240" alt="文本对话">
</p>

### 2. 语音通话

像打电话一样的纯语音交互：点开始后直接说话，说完停顿一下即被识别，回答以内置音色的语音播出。半双工（对方说话时先听完），识别、对话与语音合成全部在本机完成。

<p align="center">
  <img src="images/%E8%AF%AD%E9%9F%B3%E9%80%9A%E8%AF%9D.jpg" width="240" alt="语音通话">
</p>

### 3. 录音翻译

会议、课堂或面对面交谈时一键开始录音，边录边转写成文字并同步翻译成目标语言，结束后可用端侧大模型一键生成纪要。适合需要留档又不便把录音传到云端的场合。

<p align="center">
  <img src="images/%E5%BD%95%E9%9F%B3%E7%BF%BB%E8%AF%91.jpg" width="240" alt="录音翻译">
</p>

### 4. 本地视频字幕

导入手机里的本地视频，离线生成字幕并给出内容总结与要点提取。外语课程录播、会议录像都能在本地完成，视频本身不会离开设备。

<p align="center">
  <img src="images/%E6%9C%AC%E5%9C%B0%E8%A7%86%E9%A2%91%E5%AD%97%E5%B9%95.jpg" width="240" alt="本地视频字幕">
</p>

### 5. 跨语沟通

多人、多语言场景下的实时沟通助手：按说话人分别转写并互译，双方用各自语言说话即可看懂对方的译文，适合跨境交流、涉外接待等面对面场景。

<p align="center">
  <img src="images/%E8%B7%A8%E8%AF%AD%E6%B2%9F%E9%80%9A.jpg" width="240" alt="跨语沟通">
</p>

### 6. 实时视频听音

以悬浮窗形式实时显示正在播放内容（含系统内录音频）的字幕，支持 50 种语言。视频不出设备，边播边出字幕。

<p align="center">
  <img src="images/%E5%AE%9E%E6%97%B6%E5%90%AC%E9%9F%B3.jpg" width="240" alt="实时视频听音">
</p>

### 7. 全能扫描

文档扫描：自动边缘检测 + 透视矫正，把拍歪的纸质文件修正成规整的扫描件，为后续识别与翻译做准备。

<p align="center">
  <img src="images/%E5%85%A8%E8%83%BD%E6%89%AB%E6%8F%8F.jpg" width="240" alt="全能扫描">
</p>

### 8. 文档识别翻译

txt / Word / PDF / 图片的离线识别与翻译，支持格式还原导出，全程本地解析，适合合同、说明书等不便外传的文件。

<p align="center">
  <img src="images/%E6%96%87%E6%A1%A3%E7%BF%BB%E8%AF%91.jpg" width="240" alt="文档识别翻译">
</p>

### 研发状态

全部能力均在纯端侧离线运行，受端侧算力限制，各智能体的完成度如下：

| 名称 | 状态 | 待办 |
| --- | --- | --- |
| 文本对话智能体 | 基本可用级 | 待集成 RAG 能力 |
| 语音通话智能体 | demo 演示级 | 纯端侧语音回复间隔时间较大，尚未达到流畅级别，效率待提升或替换为实时模型 |
| 录音翻译智能体 | 基本可用级 | 语速较快时仍面临效率问题，尤其是翻译效率较低，效率待提升 |
| 本地视频字幕智能体 | 高度可用级 | 暂无 |
| 跨语沟通智能体 | 基本可用级 | 纯端侧语音翻译复述间隔较大，效率待提升或替换为实时模型 |
| 实时视频听音智能体 | demo 演示级 | 正常说话语速纯端侧跟不上，只能暂停或缓速才能使用，效率待优化 |
| 全能扫描智能体 | 基本可用级 | 能扫描常见文件，需要支持更多场景 |
| 文档识别翻译智能体 | demo 演示级 | 对文档格式还原能力基本没有，待想方案解决 |

## 二、下载 APK 直接使用

不想编译的话，直接下载预编译安装包即可（模型已内置，装完即可离线使用）：

- 文件：`xiaoxi离线AI宝.apk`
- 链接：https://pan.baidu.com/s/18Fc9oFpRzoySbjHCXCH8aA
- 提取码：`a6bb`

安装要求：Android 8.0（API 26）及以上、arm64 设备；安装时需在系统设置中允许「未知来源应用」安装。首次启动会把内置模型解包到应用目录，耗时数分钟且需要较多存储空间，建议在网络与电量充足时完成。

## 三、准备模型（编译源码必做）

模型文件**不在仓库里**（总量约 4GB）。下载 `assets.zip` 后解压，把里面的目录放到 `app/src/main/assets/` 下：

- 文件：`assets.zip`
- 链接：https://pan.baidu.com/s/1Zx1eVrAPA90UvKNPhYkzDw
- 提取码：`yk75`

```
asr/    语音识别    mt/     机器翻译    llm/    端侧大模型
tts/    语音合成    ocr/    文字识别    vad/    语音端点检测
```

目录结构与注意事项见 [`app/src/main/assets/README.md`](app/src/main/assets/README.md)。
没有模型也能编译安装，只是对应能力不可用。

## 四、编译运行

```bash
./gradlew :app:assembleDebug     # 打调试包
./gradlew :app:installDebug      # 直接安装到连接的设备
./gradlew :app:assembleRelease   # 打发布包
./gradlew :app:bundleRelease     # 打 AAB（上架 Google Play）
```

环境：JDK 11+，Android Studio 最新稳定版（AGP 8.13）。国内网络已配置阿里云 Maven 镜像。

## 五、目录结构

```
app/src/main/java/com/example/xiaoxiai/
├── MainActivity.kt        首页、路由
├── SettingsScreen.kt      设置（主题 / NPU 加速）
├── TextChatAgent.kt       文本对话
├── VoiceCallAgent.kt      语音通话
├── SpeechMT*.kt           录音翻译
├── VideoSubtitle.kt       本地视频字幕
├── CrossLangAgent.kt      跨语沟通
├── ListenSubtitle.kt      实时视频听音
├── DocTransAgent.kt       文档识别翻译
├── DocTextReader.kt       txt / Word / PDF 文本抽取
├── MarkdownText.kt        Markdown 渲染（对话、纪要等复用）
├── LlmEngine.kt           端侧大模型推理
├── TtsEngine.kt           语音合成
├── scan/                  全能扫描（OpenCV + CameraX）
└── ...                    VAD、音频 IO、分词器、文档解析等
```

## 六、开源协议

本项目代码采用 [Apache License 2.0](LICENSE) 授权，可自由使用、修改与二次分发（需保留协议声明与署名）。

> 提醒：若要上架应用市场，应用内的第三方模型与依赖（ONNX Runtime、PyTorch Mobile、OpenCV 等）
> 各自遵循其上游许可，请一并遵守；国内上架还需自备软件著作权、App 备案与隐私政策等材料。

## 七、Star History

如果这个项目对你有帮助，欢迎点个 Star ⭐

[![Star History Chart](https://api.star-history.com/svg?repos=chenking2020/xiaoxiai-android&type=Date)](https://www.star-history.com/#chenking2020/xiaoxiai-android&Date)

