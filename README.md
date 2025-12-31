# DjayNowplaying

[English](#english) | [中文](#chinese)

<a name="english"></a>

DjayNowplaying is a lightweight "Now Playing" display tool for [djay Pro](https://www.algoriddim.com/djay-pro-windows). It monitors djay Pro's local database to extract current track information and playback history, displaying them via a local web server. It is perfect for OBS streaming or personal use.

## Features

*   **Real-time Monitoring**: Directly reads `MediaLibrary.db`, no complex API configuration required.
*   **Artwork Extraction**: Automatically extracts album artwork from audio files (supports MP3, FLAC, M4A, etc., requires `mutagen`).
*   **Web Interface**: Provides a beautiful HTML page to display current playback and history, supporting OBS Browser Source.
*   **Highly Customizable**:
    *   Built-in settings interface to configure database path, port, and history count.
    *   Toggle display of History, Playback Time, and Source info via the Web interface.
    *   **Custom Skins**: Fully customize the display by modifying `template.html` (CSS/HTML).
*   **Privacy Protection**: Smartly hides sensitive "Source" paths (e.g., Explorer paths).
*   **Standalone**: Provided as a packaged EXE, ready to use out of the box.

## Installation & Usage

### Method 1: Run Directly (Recommended)

1.  Download the latest version of `DjayNowplaying.exe`.
2.  Ensure the `template.html` file is in the same directory as the EXE.
3.  Double-click to run `DjayNowplaying.exe`.
4.  After startup, click "Settings" and confirm that `djay DB Path` points to your djay database file.
    *   Usually located at: `C:\Users\<Username>\Music\djay\djay Media Library\MediaLibrary.db`
5.  Open the displayed address in your browser (Default: `http://localhost:8000`).
6.  **OBS Setup**: Add a "Browser" source in OBS, enter the URL above, and set appropriate width/height (Recommended 800x600 or custom).

### Method 2: Run from Source

If you are familiar with Python, you can run the source code directly:

1.  Clone or download this project.
2.  Install dependencies:
    ```bash
    pip install mutagen
    ```
    *(Note: `mutagen` is used for artwork extraction. The tool runs without it, but artwork won't be displayed)*
3.  Run the script:
    ```bash
    python DjayNowplaying.py
    ```

## Configuration

In the "Settings" interface, you can adjust:

*   **djay DB Path**: Absolute path to the djay media library database file.
*   **Server Port**: Web server port (Default 8000).
*   **Poll Interval**: Database polling interval.
*   **Show History**: Toggle history display on the web page.
*   **Show Time**: Toggle playback time display.
*   **Show Source**: Toggle track source display (e.g., SoundCloud, Tidal, Local).

## Custom Styling

The `template.html` file in the root directory controls the web page appearance. You can edit this file to modify layout, colors, fonts, or animations.

After saving changes, refresh the browser or refresh web area at OBS to see the effects immediately; no need to restart the program.

## Build

If you want to package the EXE file yourself:

1.  Install PyInstaller:
    ```bash
    pip install pyinstaller
    ```
2.  Run the build command:
    ```bash
    pyinstaller DjayNowplaying.spec
    ```
3.  After building, find `DjayNowplaying.exe` in the `dist` folder.
4.  **Important**: Remember to copy `template.html` to the folder where the EXE is located.

## License

MIT License

## Author

stanzas

## Support

If you find this project useful, consider giving it a star or supporting the project.

<a name="chinese"></a>

# DjayNowplaying (中文)

DjayNowplaying 是一个用于 [djay Pro](https://www.algoriddim.com/djay-pro-windows) 的轻量级“正在播放”显示工具。它通过监控 djay Pro 的本地数据库，实时提取当前播放的曲目信息和历史记录，并通过本地 Web 服务器展示，非常适合 OBS 直播推流或个人使用。

## 功能特点

*   **实时监控**：直接读取 `MediaLibrary.db`，无需复杂的 API 配置。
*   **封面提取**：自动从音频文件中提取专辑封面（支持 MP3, FLAC, M4A 等，需安装 `mutagen`）。
*   **Web 界面**：提供美观的 HTML 页面展示当前播放和历史记录，支持 OBS 浏览器源。
*   **高度可定制**：
    *   自带设置界面，可配置数据库路径、端口、历史记录数量。
    *   支持通过 Web 界面开关显示：历史记录、播放时间、来源信息。
    *   **自定义皮肤**：通过修改 `template.html` 即可完全自定义显示效果（CSS/HTML）。

## 安装与使用

### 方式一：直接运行 (推荐)

1.  下载最新版本的 `DjayNowplaying.exe`。
2.  确保 `template.html` 文件与 EXE 在同一目录下。
3.  双击运行 `DjayNowplaying.exe`。
4.  程序启动后，点击“设置” (Settings)，确认 `djay DB Path` 指向您的 djay 数据库文件。
    *   通常位于：`C:\Users\<用户名>\Music\djay\djay Media Library\MediaLibrary.db`
5.  在浏览器中访问显示的地址（默认：`http://localhost:8000`）。
6.  **OBS 设置**：在 OBS 中添加“浏览器”源，URL 填入上述地址，设置合适的宽高（推荐 800x600 或自定义）。

### 方式二：源码运行

如果您熟悉 Python，可以直接运行源码：

1.  克隆或下载本项目。
2.  安装依赖：
    ```bash
    pip install mutagen
    ```
    *(注：`mutagen` 用于提取封面，如果不安装也可以运行，但无法显示封面)*
3.  运行脚本：
    ```bash
    python DjayNowplaying.py
    ```

## 配置说明

在程序界面的“设置”中，您可以调整：

*   **djay DB Path**: djay 媒体库数据库文件的绝对路径。
*   **Server Port**: Web 服务器端口（默认 8000）。
*   **Show History**: 是否显示历史播放记录。
*   **History Count**: 显示的历史记录条数。
*   **Poll Interval**: 轮询Djay数据库的间隔。
*   **Show Time**: 是否显示播放时间。
*   **Show Source**: 是否显示曲目来源（如 SoundCloud, Tidal, Local）。

## 自定义样式

项目根目录下的 `template.html` 控制着网页的显示效果。您可以随意编辑该文件来修改布局、颜色、字体或动画。

*   **修改背景透明度**：编辑 CSS 中的 `.now-playing-card` 和 `.history-section` 的 `background` 属性，使用 `rgba()` 设置透明度。
*   **修改布局**：直接修改 HTML 结构。

修改保存后，刷新浏览器即可看到效果，无需重启程序。

## 构建 (Build)

如果您想自己打包 EXE 文件：

1.  安装 PyInstaller：
    ```bash
    pip install pyinstaller
    ```
2.  运行打包命令：
    ```bash
    pyinstaller DjayNowplaying.spec
    ```
3.  打包完成后，在 `dist` 文件夹中找到 `DjayNowplaying.exe`。
4.  **重要**：记得将 `template.html` 复制到 EXE 所在的文件夹中。

## 许可证

MIT License

## 作者

stanzas

## Support

If you find this project useful, consider giving it a star or supporting the project.
