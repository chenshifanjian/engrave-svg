# engrave-svg

图片转激光雕刻 SVG 矢量工具，兼容 EZCad。

## 功能

- 支持 PNG/JPG/JPEG/BMP/TIFF/WebP 格式
- 批量转换整个目录
- 高 DPI 适配图形界面
- 命令行批量处理
- 输出兼容 EZCad 激光雕刻软件
- 支持 Linux / Windows / macOS

## 安装

### 依赖

- Python 3.8+
- potrace（位图描边引擎）
- python-pillow（图片处理）

### Linux

```bash
# Arch Linux
sudo pacman -S python-pillow potrace

# Ubuntu / Debian
sudo apt install python3-pil potrace

# 安装 engrave-svg
pip install pillow
git clone https://github.com/你的用户名/engrave-svg.git
cd engrave-svg
chmod +x engrave-svg
sudo cp engrave-svg /usr/local/bin/
```

### Windows

1. 安装 Python 3：https://www.python.org/downloads/
2. 安装 potrace：
   - 下载：https://potrace.sourceforge.net/#downloading
   - 解压后将 `potrace.exe` 所在目录添加到系统 PATH
3. 安装 Python 依赖：
   ```cmd
   pip install pillow
   ```
4. 运行：
   ```cmd
   python engrave-svg.py -g
   ```

### macOS

```bash
# 安装依赖
brew install potrace
pip3 install pillow

# 运行
python3 engrave-svg.py -g
```

### Arch Linux (AUR)

```bash
yay -S engrave-svg
```

## 使用方法

### 图形界面

```bash
engrave-svg          # 打开 GUI
engrave-svg -g       # 同上
```

### 命令行

```bash
# 转换整个目录
engrave-svg ./图片目录/

# 转换单个文件，指定尺寸
engrave-svg ./图片.png -s 30

# 指定输出目录
engrave-svg ./images/ -o ./output/

# 调整二值化阈值（默认 128，范围 0-255）
engrave-svg ./images/ -t 100
```

### 命令行参数

| 参数 | 说明 | 默认值 |
|------|------|--------|
| `input` | 输入文件或目录 | 无（打开 GUI） |
| `-o, --output` | 输出目录 | 输入目录名_svg |
| `-s, --size` | 输出尺寸 (mm) | 50 |
| `-t, --threshold` | 二值化阈值 (0-255) | 128 |
| `-g, --gui` | 强制打开图形界面 | - |
| `-v, --version` | 显示版本号 | - |

## 示例

```bash
# 批量转换
engrave-svg ./图片目录/

# 输出到指定目录，调整尺寸和阈值
engrave-svg ./图片目录/ -o ./输出/ -s 30 -t 100
```

## 许可证

MIT License
