# UnderstandingShapes

SpreadJS支持在工作表中添加内置形状、自定义形状、连接符形状和相机形状。这些形状可用于增强数据可视化效果，并与单元格中的信息进行交互。
你可以在形状中添加文本和超链接，设置形状的布局格式，并应用不同的形状样式，如填充颜色、字体大小、水平和垂直对齐方式、边框颜色和线条宽度等。你可以通过旋转或调整形状大小来自定义形状属性；为连接符形状定义并添加连接点，以及自定义形状的边框。
以下类型的形状可应用于SpreadJS工作表。点击图片可访问相应主题：

| **形状类型** | **图片** | **描述** |
| ---- | --- | --- |
| [内置形状](gcdocsite__documentlink?toc-item-id=1771b950-7f0e-4ea5-ae7b-deb34f39ed8c) | ![basic-shape.53686a](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/5fefd5d8-238b-4c13-893b-6f22fcc5b9dd/basic-shape.53686a.8e4b81.png) | 从工作表中可用的不同类型的内置形状和几何图形（如正方形和圆形）中进行选择。 |
| [连接器形状](gcdocsite__documentlink?toc-item-id=f2edc0db-80e8-45dc-bf0f-4917974638bd) | ![connector-shape.b7785e](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/5fefd5d8-238b-4c13-893b-6f22fcc5b9dd/connector-shape.b7785e.4ccca5.png) | 使用工作表中不同的线条、箭头和连接点连接两个或多个形状，以创建独特的形状和模型，如流程图。 |
| [自定义形状](gcdocsite__documentlink?toc-item-id=2f35a670-301d-4e5b-aef3-2def89336f0f) | ![custom_shapes.74f26b](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/5fefd5d8-238b-4c13-893b-6f22fcc5b9dd/custom_shapes.74f26b.c16246.png) | 根据特定需求在工作表中添加自定义形状，并自定义形状模型以绘制和可视化图表。 |
| [照相机形状](gcdocsite__documentlink?toc-item-id=e53e0d49-f0cf-4742-bf34-aa8eab529b58) | ![camera-shape-basic.0ab154](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/5fefd5d8-238b-4c13-893b-6f22fcc5b9dd/camera-shape-basic.0ab154.9e73d0.gif) | 添加一个动态图像，该图像会反映引用区域的任何更改，以帮助在工作表中创建有用的交互式仪表板。 |
| [图片形状](gcdocsite__documentlink?toc-item-id=a49f70a5-e28b-4de0-843a-1bdbdf0fb639) | ![picture-shape.13b93e](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/5fefd5d8-238b-4c13-893b-6f22fcc5b9dd/picture-shape.13b93e.9c6185.png) | 使用PictureShape类将图片作为形状添加，这样图片也将支持形状格式化选项。 |

SpreadJS支持对形状进行各种操作，不仅能让你的工作表具有美观的外观，还能使其看起来非常专业。

| **功能** | **描述** |
| --- | --- |
| [组合形状](gcdocsite__documentlink?toc-item-id=9a2e276f-480a-40b1-8b3f-f100cc387da5) | 在工作表中组合和取消组合形状。 |
| [形状属性公式](gcdocsite__documentlink?toc-item-id=3647f22d-0475-4f28-844f-99164cebfc8e) | 在工作表中添加带有公式的内置形状和自定义形状。 |
| [形状属性链接](gcdocsite__documentlink?toc-item-id=e8e242fd-7dd6-43d5-9975-9a845160fdd3) | 通过公式中的引用将形状的属性绑定到工作表单元格。 |
| [格式化形状](gcdocsite__documentlink?toc-item-id=e3b02cea-ae0f-401f-8803-49264c88a7ae) | 在形状中添加不同类型的复合线条。 |
| [填充效果](gcdocsite__documentlink?toc-item-id=4a27b5aa-402a-41db-88a2-f665d43de126) | 在形状中添加填充效果以增强其外观。 |
| [形状中的文本](gcdocsite__documentlink?toc-item-id=43b79fd0-a4c3-4c5d-b5bf-5a6624b690a4) | 在形状中添加和编辑文本。 |
| [形状中的超链接](gcdocsite__documentlink?toc-item-id=54a77bba-e42a-470d-8493-c9f4dd49f5a2) | 在形状上添加超链接。 |
| [排列形状](gcdocsite__documentlink?toc-item-id=7d73cf88-bfa3-468d-84c4-adb1df1e01d8) | 使用形状对齐选项、分布选项或在使用多个形状时将它们与其他形状或网格对齐来调整形状位置。 |

> **注意：** 要在工作表中集成形状，需要引用gc.spread.sheets.shapes.*.*.\*.js脚本文件。

## 设置形状控制柄的可见性

当点击一个形状时，形状控制柄默认会显示。它们允许你调整形状大小、旋转或调整形状。不过，你可以通过将[showHandle](gcdocsite__documentlink?toc-item-id=350b7a46-18b3-4744-b70a-4c3a3e3a22fb#showHandle)方法设置为false（默认值为true）来隐藏形状控制柄。
此选项在调整形状大小时提供更简洁的视图，并隐藏所有控制柄。你仍然可以通过点击并拖动来选择和移动形状。
**有控制柄（左） \| 无控制柄（右）**
![shape-handle](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/5fefd5d8-238b-4c13-893b-6f22fcc5b9dd/shape-handle.4b7d08.gif)

```javascript
$(document).ready(function () {
    // 初始化Spread
    var spread = new GC.Spread.Sheets.Workbook(document.getElementById('ss'), { sheetCount: 1 });
    // 获取活动工作表
    var activeSheet = spread.getSheet(0);
    // 向活动工作表添加心形形状
    heart = activeSheet.shapes.add("Shape1", GC.Spread.Sheets.Shapes.AutoShapeType.heart, 100, 60, 200, 160);
    // 禁用形状的控制柄显示
    heart.showHandle(false);
});
```

同样，你也可以通过将[allowRotate](gcdocsite__documentlink?toc-item-id=350b7a46-18b3-4744-b70a-4c3a3e3a22fb#allowRotate)方法设置为false（默认值为true）来禁用形状的旋转控制柄。要禁用连接符形状的旋转功能，可以将[allowResize](gcdocsite__documentlink?toc-item-id=350b7a46-18b3-4744-b70a-4c3a3e3a22fb#allowResize)设置为false。
![shapeHandleRotate](/DOCUMENT_SITE_LINK_PREFIX_HERE/document-site-files/images/5fefd5d8-238b-4c13-893b-6f22fcc5b9dd/shapeHandleRotate.2a3a1b.png)

```javascript
var oval;
$(document).ready(function () {
    // 初始化Spread
    var spread = new GC.Spread.Sheets.Workbook(document.getElementById('ss'), { sheetCount: 1 });
    // 获取活动工作表
    var activeSheet = spread.getSheet(0);
    // 向活动工作表添加椭圆形形状
    oval = activeSheet.shapes.add('Shape1', GC.Spread.Sheets.Shapes.AutoShapeType.oval, 100, 60, 200, 160);
    // 将allowRotate设置为false
    oval.allowRotate(false);
});

// 使用代码更改形状角度的函数
function myFunction() {
    var x = document.getElementById('input').value;
    // x是形状旋转的角度
    oval.rotate(x);
}
```