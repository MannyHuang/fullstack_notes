## 如何实现一个简单的 webpack

- 读取文件分析模块依赖
- 对模块进行解析执行(深度遍历)
- 针对不同的模块使用相应的 loader
- 编译模块，生成抽象语法树 AST。
- 循环遍历 AST 树，拼接输出 js。

## babel 编译原理

- babylon 将 ES6/ES7 代码解析成 AST
- babel-traverse 对 AST 进行遍历转译，得到新的 AST
- 新 AST 通过 babel-generator 转换成 ES5
