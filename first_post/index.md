# First_post

# Markdown 扩展语法


**FixIt** 主题提供了一些扩展的语法便于你撰写文章。

<!--more-->

## Emoji 支持

这部分内容在 [Emoji 支持页面][emoji-support] 中介绍。

## 数学公式

{{< version 0.2.16 changed >}}

**FixIt** 基于 [$\KaTeX$][katex] 提供数学公式的支持。

在你的 [主题配置][theme-config] 中的 `[params.math]` 下面设置属性 `enable = true`,
并在文章的前置参数中设置属性 `math: true`来启用数学公式的自动渲染。

一个 `raw` 示例：

```markdown
{?{}{?{}< raw >}}行内公式：\(\mathbf{E}=\sum_{i} \mathbf{E}_{i}=\mathbf{E}_{1}+\mathbf{E}_{2}+\mathbf{E}_{3}+\cdots\){?{}{?{}< /raw >}}

{?{}{?{}< raw >}}
公式块：
\[ a=b+c \\ d+e=f \]
{?{}{?{}< /raw >}}
```

---

> Author: <no value>  
> URL: https://frizfealer.github.io/first_post/  

