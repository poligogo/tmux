
# tmux 配置文件

此 `tmux` 配置文件旨在提升 tmux 的使用體驗，包含自定義快捷鍵、狀態列顏色、滑鼠支持、歷史紀錄增量等功能。此配置適合需要高效操作和美觀狀態列顯示的 tmux 用戶。

## 安裝 tmux

在開始配置前，請先確保已安裝 tmux。以下是常見的安裝方法：

### 使用 APT 安裝 (適用於 Ubuntu / Debian)

```bash
sudo apt update
sudo apt install tmux
```

### 使用 YUM 安裝 (適用於 CentOS / RHEL)

```bash
sudo yum install tmux
```

### 使用 Homebrew 安裝 (適用於 macOS)

```bash
brew install tmux
```

安裝完成後，可以使用以下指令確認 tmux 是否已安裝成功：

```bash
tmux -V
```

## 功能概述

- **快捷鍵設定**：自定義 prefix 鍵為 `Ctrl-a`，並新增多個便捷的窗口和窗格管理快捷鍵。
- **狀態列顯示**：在狀態列中顯示主機名、日期和時間，並為不同元素配置不同顏色。
- **視窗分割與導航**：提供水平和垂直分割快捷鍵，並允許使用滑鼠操作窗格。
- **歷史紀錄限制**：增加歷史紀錄上限，以便更方便地查看過去輸入。

## 快捷鍵表格

| 功能描述                    | 通用 (Linux)          | macOS                         | Windows                        |
|-----------------------------|-----------------------|-------------------------------|--------------------------------|
| 設定新的前綴鍵 (Prefix)     | `Ctrl-a`             | `Cmd-a`                       | `Ctrl-a`                       |
| 重新載入配置文件            | `prefix + r`         | `Cmd-r`                       | `Ctrl-r`                       |
| 切換至下一個窗口            | `M-l`                | `Opt-l`                       | `Alt-l`                        |
| 切換至上一個窗口            | `M-h`                | `Opt-h`                       | `Alt-h`                        |
| 新建窗口                    | `M-j`                | `Opt-j`                       | `Alt-j`                        |
| 確認後關閉當前窗口          | `M-k`                | `Opt-k`                       | `Alt-k`                        |
| 選擇第一個窗口 (0)          | `` ` ``              | `` ` ``                       | `` ` ``                        |
| 確認後關閉當前窗格          | `x`                  | `Cmd-x`                       | `Ctrl-x`                       |
| 在當前窗格下方分割新窗格    | `prefix + -`         | `Cmd -`                       | `Ctrl -`                       |
| 在當前窗格右側分割新窗格    | `prefix + |`         | `Cmd + |`                     | `Ctrl + |`                     |
| 向左調整窗格大小            | `S-Left`             | `Shift + Left Arrow`          | `Shift + Left Arrow`           |
| 向右調整窗格大小            | `S-Right`            | `Shift + Right Arrow`         | `Shift + Right Arrow`          |
| 向下調整窗格大小            | `S-Down`             | `Shift + Down Arrow`          | `Shift + Down Arrow`           |
| 向上調整窗格大小            | `S-Up`               | `Shift + Up Arrow`            | `Shift + Up Arrow`             |
| 清除當前窗格顯示            | `C-k`                | `Cmd-k`                       | `Ctrl-k`                       |

## 配置詳解

### Prefix 鍵

將預設的 prefix 鍵從 `Ctrl-b` 修改為 `Ctrl-a`，以便於單手操作。

```tmux
unbind ^b
set -g prefix ^a
bind a send-prefix
```

### 狀態列設置

- **狀態列顏色**：
  - 狀態列背景色為灰色（`#666666`），文字顏色為亮灰色（`#aaaaaa`）
- **左側顯示**：會話名稱
- **右側顯示**：包含前綴狀態、主機名稱、日期和時間。具體顏色配置如下：
  - 分隔符號顯示為綠色
  - 主機名稱顯示為紅色
  - 日期顯示為藍色
  - 時間顯示為黃色

### 窗格邊界樣式

- 預設窗格邊界為灰色（`colour243`）
- 當前窗格邊界顏色為橘色（`colour208`）

### 滑鼠支持

啟用滑鼠支持以便於視窗和窗格的切換。

```tmux
set-option -g mouse on
```

### 歷史紀錄限制

將歷史紀錄上限設為 `102400` 行，方便在多行輸出時保持完整記錄。

```tmux
set-option -g history-limit 102400
```

## 使用說明

1. 將配置文件保存為 `~/.tmux.conf`。
2. 進入 tmux 環境，按下 `prefix + r` 重載配置，確保配置生效。
3. 使用自定義快捷鍵和滑鼠功能來操作窗口與窗格。

## 顏色配置說明

此配置中的顏色主要使用 256 色代碼，並適用於大多數終端機。若有不同的顏色偏好，可在 `status-right` 中調整顏色代碼，如 `#[fg=cyan]` 代表青色，`#[fg=magenta]` 代表紫紅色等。

## 錯誤排查

若遇到配置語法錯誤，請檢查各行是否有正確的顏色代碼格式，例如 `#[fg=color]`。此外，確保每一行配置均已完整輸入，避免缺少終止符號。

## 授權

此配置文件為開源，您可以自由修改和分發。
