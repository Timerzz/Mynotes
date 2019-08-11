# XML
- XML可以用来存放数据
- 必须要有一个根节点

## XML约束
- XML可以随便自定义标签,但是这样也许会比较混乱，所以可以导入约束文件来规定只能设置什么节点
- 约束文件有DTD和Schema两种

## DTD
- DTD文件已经逐渐淘汰了
- 基本格式
```dtd
<?xml version="1.0" encoding="utf-8" ?>

<!ELEMENT root (student*)>
<!ELEMENT student (name,age)>
<!ELEMENT name >
<!ELEMENT age >

<!ATTLIST student id #REQUIRED>
```
- DTD本质上也是一个xml
- 然后在xml中导入DTD
```xml
<?xml version="1.0" encoding="utf-8" ?>
<!DOCTYPE root SYSTEM "first.dtd">
```

## Schema .xsd文件
- schema本质上也是xml文件
```xml
<?xml version="1.0" encoding="UTF-8" ?>
<schema xmlns="http://www.w3.org/2001/XMLSchema" targetNamespace="timerzz"
        elementFormDefault="qualified">

    <element name="root">
        <complexType>
            <choice minOccurs="1" maxOccurs="10">
                <element name="student">
                    <complexType>
                        <sequence>
                            <element name="age">
                            </element>
                            <element name="name">
                            </element>
                        </sequence>
                        <attribute name="id" use="required">
                        </attribute>
                    </complexType>
                </element>
            </choice>
        </complexType>
    </element>
</schema>
```
- xmlns表示导入约束文件
- targetNamespace目标命名空间
- elementFormDefault表示是否强制约束

- <element>就是节点，complexType是子节点的类型，除了Stiring类型基本都用这个
- choice对个数限制， minOccurs最少几个，max最多几个
- sequence表示顺序排列，子节点的顺序不能乱。必须先age，后name
- attribute表示这个节点的属性，use=“required”表示student必须有id属性


### xsd的导入
- 导入是在根节点导入
```xml
<root xmlns="timerzz">
```
- 一般是命名空间空格加xsd文件名

- 一个xml可以导入多个xsd，为了区别，可以给不同的xsd取别名
```xml
<xx:root xmlns:xx="timerzz">   <!--在xmlns后面添加他的别名 -->
    <xx:student id="1001">
        <xx:age>12</xx:age>
        <xx:name>zhg</xx:name>
    </xx:student>
    <xx:student id="1002">
        <xx:age>x14</xx:age>
        <xx:name>lyl</xx:name>
    </xx:student>
</xx:root>
```
- 使用别名后，使用这个约束的节点前面要加上别名：

