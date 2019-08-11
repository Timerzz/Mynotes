# XPath

## 节点的选取

- /:当/在开头的时候，表示在根节点选取。在别的位置就和文件一样表示下一层。
- //:选取所有符合条件的后辈节点
- **.**:选取当前节点
- **..**：选取当前节点的父节点
- @：选取属性
```XPath
以下例子中School是根节点
School/Teacher:返回Teacher节点（有多个结果返回list）
//STudent:选取所有Student节点，不考虑位置
School//Age:选取School后代中所有Age节点
//@other: 选取Other属性
//Age[@Detail]:选取带有Detail属性的Age元素
```

## 谓语

- /School /Student[1]:选取School下面的第一个Student节点
- /School /Student[last()]:选取School下面的最后一个Student节点
- /School /Student[position()<3]:选取School下面的前两个Student节点
- //Student[@score='99']
- //Student[@score]/Age:选取带有属性score的Student节点的Age子节点