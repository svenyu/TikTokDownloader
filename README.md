# TikTokDownloader

**抖音视频/图集下载工具**，批量下载账号发布页或者喜欢页的视频和图集，或者单独下载链接对应的视频和图集。

# 实现功能

* ✅下载抖音无水印视频/图集
* ✅批量下载账号发布页/喜欢页作品
* ✅单独下载链接对应的作品
* ❎多账号批量下载
* ❎记录详细数据至文件

# 项目结构

```text
TikTokDownloader
├─ Configuration.py     //配置文件处理模块
├─ DataAcquirer.py      //抖音数据获取模块
├─ DataDownloader.py    //抖音作品下载模块
├─ Recorder.py          //运行日志记录模块
├─ StringCleaner.py     //过滤非法字符模块
├─ main.py              //程序启动入口
└─ settings.json        //配置文件，首次运行程序自动生成
```

# 程序说明

* 程序请求输入时，不输入内容或者输入“Q”或“q”即为退出程序
* 批量下载时，文件将会下载至账号同名文件夹（自动创建）
* 单独下载时，文件将会下载至指定名称文件夹（默认文件夹名称：Download）
* 如果资源没有描述，保存时文件名称的描述将替换为作品唯一值
* 注意区分 **账号链接** 和 **视频/图集链接**

# 抖音链接

|                  链接格式                  |   链接内容   | 有效期  |   程序支持    |
|:--------------------------------------:|:--------:|:----:|:---------:|
|     `https://v.douyin.com/字母数字组合/`     | 账号、视频、图集 | 临时有效 | 批量下载、单独下载 |
|   `https://www.douyin.com/note/纯数字`    |    图集    | 永久有效 |   单独下载    |
|   `https://www.douyin.com/video/纯数字`   |    视频    | 永久有效 |   单独下载    |
| `https://www.douyin.com/user/字母数字符号组合` |    账号    | 永久有效 |   批量下载    |

# Settings.json

|    参数    |     类型      |                                           说明                                            |
|:--------:|:-----------:|:---------------------------------------------------------------------------------------:|
|   url    |     str     |                                 账号链接，批量下载时使用（非视频/图集链接）                                  |
|   mode   |     str     |                      批量下载类型，post 代表发布页，like 代表喜欢页<br>（需要账号喜欢页公开可见）                      |
| accounts | list\[str\] | 账号链接和批量下载类型，多账号批量下载时使用<br>如: \[ \[ " url 1 ", " post " \], \[ " url 2 ", " like " \] \] |
|   root   |     str     |                                     文件保存路径，默认值：当前路径                                     |
|  folder  |     str     |                   单独下载链接的资源时，保存的文件夹名称<br>（如果文件夹不存在会自动创建，默认值：Download）                   |
|   name   |     str     |  文件保存时的命名规则，值之间使用空格分隔，默认值：发布时间-作者-描述<br>id: 唯一值；desc: 描述；create_time: 发布时间；author: 作者   |
|   time   |     str     |                 发布时间的格式，默认值：年-月-日 时.分.秒<br>（注意：Windows下文件名不能包含英文冒号“:”）                  |
|  split   |     str     |                                    文件命名的分隔符，默认值：“-”                                     |
|  music   |    bool     |                                 是否下载视频和图集的音乐，默认值：False                                  |

# 代码参考

* https://github.com/Johnserf-Seed/TikTokDownload
* https://requests.readthedocs.io/en/latest/
