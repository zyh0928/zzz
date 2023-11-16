# Oops.. Windows 10

## Keyboard shortcuts

- `win + e`: 我的电脑
- `win + r`: 运行

  | 输入             | 输出         |
  | ---------------- | ------------ |
  | **cmd**          | 命令提示符   |
  | **services.msc** | 服务         |
  | **regedit**      | 注册表编辑器 |
  | sysdm.cpl        | 系统属性     |
  | winver           | 系统信息     |
  | control          | 控制面板     |
  | notepad          | 记事本       |

- `win + s`: Cortana
- `win + x`: 菜单
- `win + i`: 设置
- `win + dot`: Emoji 表情
- `win + d`: 回到桌面

## PowerShell

- `Remove-Item (Get-PSReadlineOption).HistorySavePath`: PowerShell 清除历史记录
- `Get-NetConnectionProfile`: 查看网络连接信息

## Tips

### Pin a batch file to Start

- create a shortcut

  ```sh
  # execute batch file and close command prompt window
  cmd /c "path_to_your_batch_file"
  # command prompt will remain open after batch file finishes running
  cmd /k "path_to_your_batch_file"
  ```

### Internet Information Services (IIS)

- **服务名**：World Wide Web Publishing
- **命令行使用名**：w3svc
