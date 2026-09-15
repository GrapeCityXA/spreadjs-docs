# formula-and-function

报表在计算公式单元格时使用上下文。如果公式单元格在预览模式下有特定的上下文，公式计算将使用该上下文。这表明相同的公式可以根据上下文产生不同的结果。
以下代码示例展示了应用于 C2 单元格在不同上下文中的不同公式结果。

```javascript
templateSheet.setFormula(1, 3, "=C2");

// 上下文是 B2，B2 是销售员，所以 C2 将返回当前销售员的销售额。
templateSheet.setFormula(2, 2, "=SUM(C2)");

// 上下文是 A2，A2 是地区，所以 C2 将以数组形式返回当前地区的销售额。
templateSheet.setFormula(2, 3, "=C2");

// 无上下文，所以 C2 将以数组形式返回所有销售额。
templateSheet.setFormula(4, 3, "=C2");
templateSheet.setFormula(5, 3, "SUM(C2)");

reportSheet.refresh();
```

下面的图像描绘了这种上下文是如何影响公式计算的。
![image](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/ca82939a-5d1a-4838-9f3f-69a0f7ebeeb5/image.5ececf.png)
通过分层单元格索引公式，您可以在结构化的单元格排列中获取单元格的值、索引或排名。报表还提供了获取分页详情的函数，如当前页码和总页数。
此外，您可以使用报表定义模板单元格的别名，这使得在公式中使用它变得更加容易。