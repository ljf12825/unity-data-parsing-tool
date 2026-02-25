# unity-data-parsing-tool

## 这是什么

这是一个Unity本地配置表序列化/反序列化工具\
可以处理以下来源的数据

- 本地文件（Assets/Streaming/PersistentDataPath）
- 配置表

支持以下格式

- JSON
- CVS
- Binary
- ScriptableObject

使用方式

- 代码读取
- 编辑器写回
- 支持热更新/热加载
- 编辑器窗口扩展可视化修改配置
- 格式转换
- Binary序列化

## Unity中序列化的局限性

Unity的`[Serializable]`

- 不支持Dictionray
- 不支持堕胎
- 不支持私有字段（除非`[SerializeField]`）
- 不能直接存文件（只能存资产）

所以，不要指望Unity原生序列化做配置系统

```
ConfigSystem
├── Format（格式层）
│   ├── JsonFormatter
│   ├── CsvFormatter
│   └── BinaryFormatter
│
├── Storage（存储层）
│   ├── FileStorage
│   ├── PlayerPrefsStorage（可选）
│
├── Loader（加载层）
│   └── ConfigLoader<T>
│
└── Config（数据定义层）
    └── 各种配置结构体 / 类
```
