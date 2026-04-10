# Super-RearScreen-Island-Todo (超级背屏岛Pro)

> [适配Todo便签] 超级背屏岛Pro：可以在背屏显示超级岛内容的背屏主题。

专为 **小米 17 Pro 系列**（背屏机型）深度定制的 HyperOS 背屏主题部件。本模块通过接管底层焦点通知（Focus Params），将前台的「灵动岛/超级岛」状态完美映射至背屏，让你在手机倒扣时也能实时掌握外卖、打车、待办等关键进度。

---

## ✨ 核心特性

* **🔄 完美映射超级岛**：无缝解析系统 `param_v2` 和 `bigIslandArea` 数据，将主屏幕的焦点通知实时同步至背屏显示。
* **📝 深度适配 Todo便签**：针对包名 `com.farplace.todonote` 进行深度逻辑优化，精准提取标题、副标题与进度信息。
* **🍔 智能品牌识别系统**：内置强大的关键词匹配引擎。自动识别外卖品牌并加载专属视觉资产（Logo 与背景）。
* **🌙 丝滑 AOD 息屏显示**：依托小米底层 **Folme 动画引擎**，支持亮屏与 AOD 息屏状态（极低功耗，刷新率降至 0fps）的平滑过渡与透明度切换。
* **📐 动态自适应布局**：内置基于 `view_width` 和 `view_height` 的自适应缩放算法（Scale），完美兼容不同比例的背屏尺寸。

---

## 🏪 已支持的品牌库

目前代码已内置以下主流餐饮/茶饮品牌的关键词识别与专属图标映射：

* **茶饮/咖啡**：古茗、瑞幸 (Luckin)、喜茶 (Heytea)、爷爷不泡茶、一点点、CoCo、霸王茶姬 (Chagee)、茶百道、沪上阿姨、蜜雪冰城、库迪 (Cotti)
* **快餐/汉堡**：肯德基 (KFC)、麦当劳 (McDonald's)、汉堡王 (Burger King)、塔斯汀 (Tastien)

> **💡 提示**：若未匹配到已知品牌，系统将自动回退至默认样式（`default_food`）。

---

## 📱 设备兼容性

* **目标设备**：小米 17 Pro 系列（及其他搭载背屏模块的 HyperOS 机型）
* **系统要求**：Xiaomi HyperOS (需支持底层焦点通知与 Folme 动画接口)
* **依赖应用**：Todo便签 (`com.farplace.todonote`)

---

## 🛠️ 安装与使用

1. 下载本项目的 `.mrc` / `.mtz` 主题文件包。
2. 打开手机内置的 **「主题壁纸」** App。
3. 进入 **我的 -> 模块混搭 -> 背屏显示**（或直接导入本地主题包）。
4. 选择 **「Super-RearScreen-Island-Todo」** 并应用。
5. 在前台运行「Todo便签」或触发外卖状态，将手机翻转即可在背屏查看效果。

---

## 💻 开发者说明

如果你需要在此代码基础上进行二次开发（如添加新品牌）：

1. 定位到 XML 中的 `<Function name="set_line1_text">` 节点。
2. 参照现有逻辑添加新的 `MultiCommand` 分支：
   ```xml
   <MultiCommand condition="(strIndexOf(@raw_brand, '你的新品牌') } -1)">
     <VariableCommand name="enterprise_name" expression="'your_brand_name'" type="string"/>
   </MultiCommand>

```
3. 将对应的品牌 Logo 命名为 your_brand_name.png，并放置于主题包的 assets/todonote/ 目录下。
