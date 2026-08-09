# Maapvz_User_md
MaaPvz 用户文档 — 完整开发规范 & 维护指南
📋 项目概述
项目名称
MaaPvz 用户文档

项目定位
植物大战僵尸自动化工具（MaaPvz）的用户手册网站，提供从安装到高级功能的完整使用教程。

技术栈
纯静态 HTML + CSS + JavaScript

无需构建工具，直接部署到 GitHub Pages

第三方服务：Abacus API（访问计数）

仓库结构
text
Maapvz_User_md/
├── index.html                    # 主页（用户手册）
├── 无尽/
│   └── 无尽挑战.html              # 无尽挑战专项页面
├── index_iamges/                 # 主页图片资源
│   ├── PVZAA.png                 # 导航栏 Logo
│   ├── 主界面说明.png
│   ├── 植物探险.png
│   ├── 碎片挑战.png
│   ├── 双人对决.png
│   ├── 日志清理.png
│   └── 定向测序列.png
└── 无尽/images/                  # 无尽挑战页面图片
    ├── 原大_卡槽.png
    ├── 塔焦卡槽.png
    ├── 心塔_卡槽1.png
    ├── 心塔_卡槽2.png
    ├── 心塔阵容1.png
    └── 心塔阵容2.png
🎨 设计规范
颜色主题（草木绿）
所有颜色变量定义在 :root 中，修改一处即可全局生效：

变量名	当前值	用途
--brand-color	#6E9A7A	主品牌色（链接、按钮、激活状态）
--brand-color-light	#95BFA0	浅品牌色（边框、悬停）
--brand-color-dark	#4E7A5A	深品牌色（普通链接、强调文字）
--brand-color-tint	rgba(110,154,122,0.16)	品牌色透明（背景、标记）
--bg-color	#ffffff	纯白背景
--bg-color-soft	#f4f7f6	软背景（卡片、横幅）
--bg-color-mute	#e8eeec	哑光背景（悬停效果）
--text-color-1	#242424	主文字色
--text-color-2	rgba(0,0,0,0.7)	次要文字色
--text-color-3	rgba(60,60,60,0.33)	辅助文字色
--divider-light	rgba(0,0,0,0.12)	浅分割线
渐变背景
css
body {
    background: linear-gradient(180deg, #f5faf7 0%, #dce8e0 100%);
}
字体
基础字体："Inter var experimental", "Inter var", -apple-system, ...

等宽字体：Menlo, Monaco, Consolas, "Courier New", monospace

圆角
变量名	值	用途
--radius	1rem	标准圆角（卡片、提示框）
--radius-small	0.5rem	小圆角（按钮、标签）
--radius-large	1.5rem	大圆角（大按钮）
尺寸
变量名	值
--nav-height	64px
--sidebar-width	280px
--content-max-width	1000px
--content-padding-x	80px
--content-padding-y	48px
🧭 导航栏规范
位置
页面顶部，固定定位（sticky）。

结构
html
<header class="rp-nav">
    <div class="rp-nav__left">
        <div class="rp-nav__title">
            <a href="#" class="rp-nav__title__link">
                <img src="index_iamges/PVZAA.png" alt="MaaPvz Logo" style="height:32px; width:auto;" />
                <span style="font-size:1.2rem; font-weight:600;">MaaPvz 用户文档</span>
            </a>
        </div>
    </div>
    <div class="rp-nav__right">
        <a href="#" style="font-weight:500; color:var(--text-color-1);">首页</a>
        <a href="#" style="font-weight:500; color:var(--text-color-1);">用户手册</a>
        <a href="#" style="font-weight:500; color:var(--text-color-1);">开发文档</a>
        <a href="#" style="font-weight:500; color:var(--text-color-1);" target="_blank">GitHub ↗</a>
    </div>
</header>
修改指南
修改 Logo 图片
html
<!-- 替换 src 路径即可 -->
<img src="你的图片路径.png" alt="Logo" style="height:32px; width:auto;" />
修改 Logo 文字
html
<!-- 修改 span 内容 -->
<span style="font-size:1.2rem; font-weight:600;">新品牌名称</span>
添加/删除导航菜单项
html
<!-- 在 .rp-nav__right 内添加或删除 -->
<a href="#" style="font-weight:500; color:var(--text-color-1);">菜单名</a>
📂 侧边栏规范
位置
页面左侧，固定定位（sticky），高度填满视口。

结构层级
text
📖 目录导航
├── ⚠️ 使用前必看        ← 强调链接，跳转至 #快速开始
├── ▼ 新手上路           ← 可折叠父级
│   ├── 签到
│   ├── 免广告卡
│   ├── 植物探险
│   ├── 碎片挑战
│   ├── 潘妮秘宝
│   ├── 刷胜场/金币
│   ├── 幸运宝藏
│   ├── 创意庭院
│   ├── 旅行原木
│   ├── ▼ 小工具          ← 二级可折叠父级
│   │   └── 无尽测定向序列
│   ├── 日志清理
│   ├── 双人对决
│   ├── 时空秘境
│   └── 进阶设置
├── 🏰 无尽挑战（入口）   ← 独立链接
├── 如何参与开发          ← 独立链接
└── 鸣谢                 ← 独立链接
可折叠父级 HTML 模板
一级父级
html
<div class="sidebar-folder" id="folder-唯一ID" onclick="toggleFolder('folder-唯一ID')">
    <span>父级名称</span>
    <span class="arrow" id="arrow-唯一ID">▶</span>
</div>
<div class="sidebar-children" id="children-唯一ID">
    <a href="#锚点ID">子项1</a>
    <a href="#锚点ID">子项2</a>
</div>
二级父级（缩进）
html
<div class="sidebar-folder" id="folder-唯一ID" onclick="toggleFolder('folder-唯一ID')" style="background:transparent; color:var(--text-color-2); font-weight:500; padding:4px 12px;">
    <span>二级父级</span>
    <span class="arrow" id="arrow-唯一ID">▶</span>
</div>
<div class="sidebar-children" id="children-唯一ID" style="padding-left:4px;">
    <a href="#锚点ID" class="sidebar-sub">子项</a>
</div>
独立链接
html
<a href="#锚点ID" class="sidebar-link">链接名称</a>
强调链接（“使用前必看”专用）
html
<a href="#快速开始" class="sidebar-link-urgent">⚠️ 使用前必看</a>
注意：#快速开始 是固定的锚点，跳转到正文的“快速开始”章节。

添加新章节的步骤
在正文中添加标题（H2 或 H3）

html
<h2 id="新章节ID">
    <a href="#新章节ID" class="rp-header-anchor" style="color:var(--brand-color); margin-right:6px; opacity:0.6; border-bottom:none;">#</a>
    新章节名称
</h2>
在侧边栏中添加链接

如果是独立章节：在 <nav> 中添加 <a href="#新章节ID" class="sidebar-link">新章节名称</a>

如果是父级：使用 sidebar-folder 模板

如果是子项：在对应的 sidebar-children 中添加

在目录（Table of Contents）中添加条目

html
<li><a href="#新章节ID">新章节名称</a></li>
📄 文档正文规范
标题层级
层级	HTML 标签	字号	使用场景
H1	<h1>	2rem	页面主标题（“新手上路”）
H2	<h2>	1.75rem	一级章节（“快速开始”、“主要功能”）
H3	<h3>	1.5rem	二级章节（“签到”、“植物探险”）
H4	<h4>	1.25rem	三级章节（“模式一：埃及1”）
标题锚点格式
html
<h2 id="快速开始">
    <a href="#快速开始" class="rp-header-anchor" style="color:var(--brand-color); margin-right:6px; opacity:0.6; border-bottom:none;">#</a>
    快速开始
</h2>
提示框（Callout）
类型	类名	用途
提示	rp-callout rp-callout--tip	建议、技巧
信息	rp-callout rp-callout--info	说明、补充
警告	rp-callout rp-callout--warning	注意事项
危险	rp-callout rp-callout--danger	重要警告、Bug 提示
示例：

html
<div class="rp-callout rp-callout--tip">
    <div class="rp-callout__title">💡 建议</div>
    <div class="rp-callout__content">
        <p>这里是提示内容。</p>
    </div>
</div>
图片插入
html
<img src="index_iamges/图片名.png" alt="图片描述" />
图片大小建议：宽度不超过 1000px，保持合理比例。

任务列表（Checklist）
html
<ul class="contains-task-list">
    <li class="task-list-item"><input disabled="" type="checkbox" checked="" /> 已完成的项</li>
    <li class="task-list-item"><input disabled="" type="checkbox" /> 未完成的项</li>
</ul>
代码块
html
<pre><code>// 示例代码
function hello() {
    console.log("Hello World!");
}</code></pre>
📊 访问计数器规范
技术方案
服务商：Abacus API

接口地址：https://abacus.jasoncameron.dev

命名空间：maapvz

计数器类型
类型	Key 格式	用途
当日计数	daily-YYYY-MM-DD	统计当天独立访客数
累计总数	total	统计所有历史独立访客数
去重逻辑
使用 localStorage 记录：

键名	用途
maapvz_visit_date	记录最后一次访问日期
maapvz_daily_counted	标记当天是否已计（true/false）
maapvz_total_counted	标记是否已计累计（true/false）
maapvz_daily_cache	缓存当天计数（用于降级）
maapvz_total_cache	缓存累计计数（用于降级）
核心逻辑
javascript
// 1. 检查本地标记
// 2. 未计过 → 调用 hit 接口（+1）
// 3. 已计过 → 调用 get 接口（只获取）
// 4. API 失败 → 降级到 localStorage
显示格式
text
🌟 今天第 X 个打开 | 📌 累计 X 人 ✨ 自己查阅文档的样子真的很棒！
手动测试 API
bash
# 获取当日计数
https://abacus.jasoncameron.dev/get/maapvz/daily-YYYY-MM-DD

# 增加当日计数
https://abacus.jasoncameron.dev/hit/maapvz/daily-YYYY-MM-DD

# 获取累计计数
https://abacus.jasoncameron.dev/get/maapvz/total

# 增加累计计数
https://abacus.jasoncameron.dev/hit/maapvz/total
🔧 常用修改指南
修改主色调
在 :root 中修改：

css
--brand-color: #6E9A7A;
--brand-color-light: #95BFA0;
--brand-color-dark: #4E7A5A;
--brand-color-tint: rgba(110, 154, 122, 0.16);
修改渐变背景
在 body 样式中修改：

css
background: linear-gradient(180deg, #f5faf7 0%, #dce8e0 100%);
调整图片路径
图片统一放在 index_iamges/ 目录下，引用格式：

html
<img src="index_iamges/文件名.png" />
修改导航栏文字
html
<span style="font-size:1.2rem; font-weight:600;">新名称</span>
修改“使用前必看”跳转目标
html
<!-- 修改 href 的锚点 -->
<a href="#快速开始" class="sidebar-link-urgent">⚠️ 使用前必看</a>
添加新图片到页面
将图片放入 index_iamges/ 目录

在正文中插入：

html
<img src="index_iamges/新图片.png" alt="描述" />
🚀 部署指南
部署到 GitHub Pages
提交代码：

bash
git add .
git commit -m "更新文档"
git push origin main
启用 GitHub Pages：

仓库 → Settings → Pages

Branch: main，目录: / (root)

点击 Save

访问地址：

text
https://daoyanxiaoz.github.io/Maapvz_User_md/
本地预览
直接双击 index.html 在浏览器中打开即可。

📝 代码片段速查
新增一个 H2 章节
html
<h2 id="章节ID">
    <a href="#章节ID" class="rp-header-anchor" style="color:var(--brand-color); margin-right:6px; opacity:0.6; border-bottom:none;">#</a>
    章节名称
</h2>
<p>章节内容...</p>
新增一个 H3 子章节
html
<h3 id="子章节ID">
    <a href="#子章节ID" class="rp-header-anchor" style="color:var(--brand-color); margin-right:6px; opacity:0.6; border-bottom:none;">#</a>
    子章节名称
</h3>
<p>子章节内容...</p>
新增侧边栏独立链接
html
<a href="#章节ID" class="sidebar-link">链接名称</a>
新增侧边栏折叠父级
html
<div class="sidebar-folder" id="folder-唯一ID" onclick="toggleFolder('folder-唯一ID')">
    <span>父级名称</span>
    <span class="arrow" id="arrow-唯一ID">▶</span>
</div>
<div class="sidebar-children" id="children-唯一ID">
    <a href="#子项ID">子项1</a>
    <a href="#子项ID">子项2</a>
</div>
更新目录（Table of Contents）
html
<li>
    <a href="#父级ID">父级名称</a>
    <ul>
        <li><a href="#子项ID">子项名称</a></li>
    </ul>
</li>
⚠️ 注意事项
锚点 ID 必须唯一：每个标题的 id 不能重复，否则侧边栏跳转会错乱。

图片路径区分：

主页图片：index_iamges/

无尽挑战图片：无尽/images/

侧边栏折叠 ID 命名规范：

父级：folder-xxx

子项容器：children-xxx

箭头：arrow-xxx

“使用前必看”固定跳转：始终指向 #快速开始，不要修改。

访问计数器：

命名空间 maapvz 如需重置，改为新名称（如 maapvz2026）

当日计数每天自动重置

响应式：侧边栏在屏幕宽度 < 1024px 时自动隐藏。

📞 联系与支持
聊天群：669689256

开发群：1092806752

GitHub：https://github.com/daoyanxiaoz/Maapvz_User_md

最后更新：2026-08-09