# 简介

这是一个用于将翻译数据从 CSV 文件转换为 JSON 文件的工具。它可以读取一个包含翻译数据的 CSV 文件，并将数据转换为两个 JSON 文件，分别是英文版和中文版。转换后的 JSON 文件可以在本地文件夹中找到。

## 依赖

- fs
- csv-parser
- prettier


## 使用方法

1. 在项目目录下终运行以下命令，安装所需的依赖项：

   ```
   npm install fs csv-parser prettier
   ```

2. 修改translations.csv文件内容为你需要翻译的内容，第一列版本号，第二列为备注，第三列英文，第四列中文。

3. 将translations.csv文件放在与代码文件相同的目录中。

4. 在终端中运行以下命令，以将CSV文件转换为JSON格式的翻译文件：

   ```
   node translationConverter.js
   ```

5. 将在名为“local”的目录中生成两个文件：en.json和zh.json。这些文件将包含英文和中文翻译内容的JSON格式。

6. 请查看转换结果并在需要的情况下进行修改。

7. 注意：如果CSV文件中存在任何错误或缺失的数据，代码将输出警告消息并停止转换过程。如果发现任何问题，请检查CSV文件中


## 常量定义

- EN_FILE：英文版 JSON 文件名
- ZH_FILE：中文版 JSON 文件名
- CSV_FILE：待转换的 CSV 文件名
- LOCAL_DIR：本地文件夹名

## 变量说明

- en：存储英文版数据的对象
- zh：存储中文版数据的对象
- totalRows：CSV 文件总行数
- validRows：有效行数
- usedIds：已使用的翻译 ID 列表

## 流程说明

1. 创建本地文件夹，用于存储转换后的 JSON 文件。
2. 读取 CSV 文件并进行解析。
3. 检查每一行的翻译 ID 是否为空，是否重复，英文版和中文版的值是否为空。
4. 将有效的翻译数据添加到 en 和 zh 对象中，并记录已使用的翻译 ID。
5. 检查是否存在中文翻译和英文翻译。
6. 格式化输出转换后的 JSON 文件。
7. 将转换后的 JSON 文件写入本地文件夹。
8. 输出转换结果和错误信息（如果有的话）。

## 注意事项

- CSV 文件必须包含 id、en-us 和 zh-cn 列。
- 该脚本不会覆盖已存在的同名 JSON 文件，如果需要更新，请手动删除已存在的文件后再次运行脚本。
- 如果转换过程中出现错误，脚本将会停止运行并输出错误信息。请检查 CSV 文件中的错误数据并重新运行脚本。
