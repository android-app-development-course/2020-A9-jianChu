# 简厨（JianChu）

> 一款轻量级菜谱工具应用，面向厨房新手与选择困难症用户，提供简洁直观的菜谱浏览与烹饪指导。

**移动应用开发课程项目 — 第9小组**

---

## 功能特性

- **🏠 首页菜谱浏览** — 横向卡片流展示推荐菜谱，一键查看详情
- **📋 菜谱列表** — 双列网格布局，按早/午/晚餐分类浏览全部菜谱
- **📖 菜谱详情** — 封面图、准备时间、烹饪时间、原料清单、步骤指南一览无余
- **🔔 定时提醒** — 自定义三餐提醒时间（早餐 08:30 / 午餐 12:30 / 晚餐 20:31），系统闹钟准时推送通知
- **📤 一键分享** — 将菜谱信息分享至微信、QQ 等社交平台
- **🎨 流畅动效** — MotionLayout 驱动的侧边栏滑入动画

## 技术栈

| 类别 | 技术 |
|------|------|
| 语言 | Kotlin 1.3.72 |
| 最低支持 | Android 5.0（API 22） |
| 目标平台 | Android 10（API 29） |
| 架构 | MVVM（ViewModel + LiveData + Repository） |
| UI | AndroidX + Material Design + ConstraintLayout + MotionLayout |
| 导航 | Jetpack Navigation Component |
| 网络 | Retrofit 2 + Gson + OkHttp |
| 图片 | Coil |
| 异步 | Kotlin Coroutines |
| 定时 | AlarmManager + BroadcastReceiver |
| 构建 | Gradle 6.5 + AGP 4.1.1 |

## 项目结构

```
app/src/main/java/it/cook/
├── MainActivity.kt                  # 主入口，DrawerLayout + MotionLayout
├── model/                          # 数据模型
│   ├── Recipe.kt                   # 菜谱实体
│   ├── RecipeData.kt               # 菜谱列表包装
│   └── Status.kt                   # 请求状态（Loading/Success/Error）
├── network/                        # 网络层
│   ├── ApiService.kt               # Retrofit API 定义
│   └── RetrofitBuilder.kt          # Retrofit 单例
├── receiver/                       # 闹钟与通知
│   ├── AlarmHandler.kt             # 定时设置
│   └── AlarmReceiver.kt            # 广播接收 → 发送通知
├── repository/
│   └── MainRepository.kt           # 数据仓库
├── ui/                             # 界面层
│   ├── HomeFragment.kt             # 首页
│   ├── ListFragment.kt             # 菜谱列表
│   ├── DetailFragment.kt           # 菜谱详情
│   ├── PreferencesFragment.kt      # 偏好设置
│   ├── AboutFragment.kt            # 关于页面
│   └── adapter/                    # RecyclerView 适配器
├── utils/                          # 工具类
│   ├── Constants.kt                # 全局常量
│   ├── DrawerContent.kt            # 自定义 MotionLayout
│   ├── NotificationUtils.kt        # 通知发送
│   └── ViewModelFactory.kt          # ViewModel 工厂
└── viewmodel/                      # ViewModel 层
    ├── MainViewModel.kt             # 菜谱数据管理
    └── NavDrawerState.kt            # 抽屉状态
```

## 页面预览

### 首页
首页展示圆角悬浮 App Bar 和横向滚动菜谱卡片，底部显示团队签名。点击「SEE ALL」进入完整列表，点击汉堡菜单打开侧边栏。

### 菜谱详情
展示菜品封面大图、名称、准备/烹饪时间、原料清单和分步烹饪指南。底部「分享菜谱」按钮可调用系统分享面板。

### 偏好设置
三张卡片分别对应早餐、午餐、晚餐的定时提醒开关。开关状态自动保存，开启后通过 AlarmManager 在设定时间推送系统通知。

### 侧边栏
采用 MotionLayout + DrawerLayout 实现平滑滑入动画，提供主页、偏好、关于三个导航入口。

## 构建与运行

### 环境要求

- Android Studio 4.1+
- JDK 8
- Android SDK（API Level 29）
- Gradle 6.5

### 步骤

```bash
# 克隆仓库
git clone https://github.com/android-app-development-course/2020-A9-jianChu.git

# 用 Android Studio 打开项目
# 或使用命令行构建
cd 2020-A9-jianChu
./gradlew assembleDebug
```

## 菜谱数据

菜谱数据存储于 [`db.json`](db.json)，通过 [my-json-server](https://my-json-server.typicode.com/) 提供 REST API 服务。


## 相关文档

| 文档 | 说明 |
|------|------|
| [第9小组UI设计制作文档](第9小组UI设计制作文档.md) | UI 设计规范、页面结构、交互流程、组件标准 |
| [简厨应用方案设计](简厨应用方案设计.md) | 产品定位、功能规划、技术方案 |

## License

本项目为课程教学项目，仅供学习参考。
