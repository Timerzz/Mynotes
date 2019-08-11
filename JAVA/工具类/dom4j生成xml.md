# dom4j
- dom4j用来操作xml文件
- 需要导入dom4j.jar和jaxen.jar
## 生成xml的方法
- 首先获得Document对象
- 在Document对象中添加第一个元素作为根节点
- 在每个节点将继续添加子节点
- addAttribute方法可以添加属性
```java
 var doc= DocumentHelper.createDocument();
var root=doc.addElement("root");
for(int i=0;i<3;i++) {
    var student = root.addElement("name");   //添加子节点
    student.addAttribute("id", i+"");    //添加id属性和值
    student.addElement("name").setText(""+18+i);   //添加name子节点和值
    student.addElement("name").setText("zhg"+i);
}
```

## 写入xml的方法
- 首先声明一个OutputFormat对象，作为格式化对象
- 声明XMLWriter用来写入
```java
var format=new OutputFormat();    //声明格式化输入对象
format.setNewlines(true);    //新节点是否换行
format.setIndent(true);     //是否缩进

var writer=new XMLWriter(new FileWriter(new File("test.xml")),format);
writer.write(doc);    //将Document对象写入
writer.close();    //关闭
```

## 读取xml
- 读取xml用的是SAXReader对象
- getRootElement()获得根节点
- element.attributeValue("id")可以获得节点的属性的值
- .elements()方法获得该节点的所有子节点，返回的是list对象
- element1.getName()返回这个节点的名字
- element1.getText()返回这个节点的值
```java
public class TestReaderXML {
    public static void main(String[] args) throws FileNotFoundException, DocumentException {
        var Reader= new SAXReader();    //获得SAXReader对象
        var doc=Reader.read("stus.xml");//读取xml文件
        var root=doc.getRootElement();   //获得根节点

        var list=root.elements();     //获得根节点的所有子节点
        for (Element element : list) {
            System.out.println(element.attributeValue("id"));
            var stulist=element.elements();
            for (Element element1 : stulist) {
                System.out.print(element1.getName());
                System.out.println(element1.getText());
            }
        }
    }
}
```