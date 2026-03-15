# Android TextView 文本视图演示

## 简介

本 Demo 演示 TextView 的基本用法和常用属性。

## 基本原理

TextView 是 Android 最基本的文本显示组件，用于在界面上展示文本。它是 EditText、Button 等组件的基类。

常用属性：
- `text`：文本内容
- `textSize`：字体大小
- `textColor`：字体颜色
- `textStyle`：字体样式（粗体、斜体）
- `gravity`：对齐方式
- `maxLines`：最大行数
- `ellipsize`：文本省略方式

## 启动和使用

### 环境要求
- Android Studio
- JDK 17
- Gradle 8.x

### 安装和运行

1. 用 Android Studio 打开项目
2. 连接 Android 设备或模拟器
3. 点击 Run 运行

### 使用方法
- 运行后将看到不同样式的文本显示

## 教程

### 什么是 TextView？

TextView 是 Android UI 的基础组件，用于显示文本内容。虽然功能简单，但通过组合各种属性可以实现丰富的显示效果。

### 常用属性

```xml
<TextView
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:text="文本内容"
    android:textSize="18sp"
    android:textColor="#FF0000"
    android:textStyle="bold"
    android:gravity="center"
    android:padding="16dp"
    android:maxLines="2"
    android:ellipsize="end" />
```

### 样式说明

- **textSize**：字体大小，单位推荐使用 sp
- **textColor**：字体颜色，可以使用颜色值或颜色资源
- **textStyle**：字体样式，bold（粗体）、italic（斜体）
- **gravity**：对齐方式，center、left、right、top、bottom
- **ellipsize**：省略方式，end（尾部省略）、start（头部省略）、middle（中间省略）

### HTML 格式化

TextView 支持部分 HTML 标签：

```kotlin
textView.text = Html.fromHtml(
    "这是普通文本<br>" +
    "<b>粗体文本</b><br>" +
    "<i>斜体文本</i><br>" +
    "<u>下划线文本</u>"
)
```

### 可点击文本

```xml
<TextView
    android:text="点击这里"
    android:textColorLink="@color/blue"
    ... />
```

设置点击监听：

```kotlin
textView.movementMethod = LinkMovementMethod.getInstance()
```

## 关键代码详解

### MainActivity.kt

```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        // 获取 TextView 组件
        val textView = findViewById<TextView>(R.id.textView)

        // 设置文本内容，使用换行符分隔
        // TextView 支持 \n 换行
        textView.text = """
            这是普通文本

            <b>粗体文本</b>
            <i>斜体文本</i>
            <u>下划线文本</u>
        """.trimIndent()

        // 注意：上面的字符串包含 HTML 标签
        // 实际渲染时需要用 Html.fromHtml() 处理
    }
}
```

### activity_main.xml

```xml
<!-- 使用 ScrollView 包裹，支持滚动 -->
<ScrollView xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="16dp">

    <!-- TextView 组件 -->
    <TextView
        android:id="@+id/textView"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="TextView 文本视图演示"
        android:textSize="18sp" />
</ScrollView>
```

### 常用属性速查表

| 属性 | 说明 | 示例 |
|------|------|------|
| android:text | 文本内容 | android:text="Hello" |
| android:textSize | 字体大小 | android:textSize="18sp" |
| android:textColor | 字体颜色 | android:textColor="#FF0000" |
| android:textStyle | 字体样式 | android:textStyle="bold" |
| android:gravity | 对齐方式 | android:gravity="center" |
| android:padding | 内边距 | android:padding="16dp" |
| android:maxLines | 最大行数 | android:maxLines="2" |
| android:ellipsize | 省略方式 | android:ellipsize="end" |
