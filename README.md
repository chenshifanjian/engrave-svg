# engrave-svg

> 图片转激光雕刻 SVG 矢量工具，兼容 EzCad

一个轻量的图片转矢量工具，支持批量转换，生成的 SVG 可直接导入 EzCad 等激光雕刻软件使用。

## 截图

<!-- 如果有的话可以加上 -->

## 特性

- 支持 PNG / JPG / BMP / TIFF / WebP 格式
- 批量转换整个目录
- 图形界面（高 DPI 适配）+ 命令行双模式
- 透明背景自动处理为白色
- 二值化阈值可调（控制细节保留程度）
- 输出尺寸可自定义（默认 50mm）

## 安装

### 依赖

- Python 3.8+
- [potrace](https://potrace.sourceforge.net/) — 位图描边引擎
- [Pillow](https://python-pillow.org/) — 图片处理

### Arch Linux

```bash
sudo pacman -S python-pillow potrace
```

### Ubuntu / Debian

```bash
sudo apt install python3-pil potrace
```

### macOS

```bash
brew install potrace
pip3 install pillow
```

### Windows

1. 安装 [Python 3](https://www.python.org/downloads/)
2. 下载 [potrace](https://potrace.sourceforge.net/#downloading)，将 `potrace.exe` 所在目录添加到系统 PATH
3. `pip install pillow`

### 从源码运行

```bash
git clone https://github.com/chenshifanjian/engrave-svg.git
cd engrave-svg
chmod +x engrave-svg
./engrave-svg        # 打开 GUI
```

### AUR (Arch Linux)

> AUR 包正在等待审核上架，暂时请使用 [Release](https://github.com/chenshifanjian/engrave-svg/releases) 下载。

```bash
# 等上架后可用：
yay -S engrave-svg
```

## 使用

### 图形界面

```bash
./engrave-svg
# 或
./engrave-svg -g
```

### 命令行

```bash
# 转换整个目录
./engrave-svg ./图片目录/

# 转换单个文件，指定尺寸
./engrave-svg ./图片.png -s 30

# 指定输出目录
./engrave-svg ./images/ -o ./output/

# 调整二值化阈值（0-255，默认 128）
# 阈值越低保留越多细节，越高越简洁
./engrave-svg ./images/ -t 100
```

### 参数

| 参数 | 说明 | 默认值 |
|------|------|--------|
| `input` | 输入文件或目录 | 无（打开 GUI） |
| `-o, --output` | 输出目录 | `输入目录名_svg` |
| `-s, --size` | 输出尺寸 (mm) | 50 |
| `-t, --threshold` | 二值化阈值 | 128 |
| `-g, --gui` | 打开图形界面 | — |
| `-v, --version` | 版本号 | — |

## 原理

1. 读取图片，处理透明通道（RGBA → 白底 RGB）
2. 转为灰度图，按阈值二值化
3. 调用 potrace 描边生成 SVG 路径
4. 设置输出尺寸为指定毫米值

## 许可

[MIT](LICENSE)
