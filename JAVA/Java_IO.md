# 字符流
##  文件IO

- 文件夹检测存在与创建
```java
String FilePath="file";    //文件夹路径
File file=new File(FilePath);
if(!file.exists()) {     //如果不存在
    file.mkdirs();
}
```

- 文件创建

```java
  String FileName="abc.txt";    //文件路径
  file=new File(FilePath+File.separator+FileName);
  if(!file.exists()) {
      file.createNewFile();
  }
```

- 文件的写入 writer

```java
FileWriter fw=new FileWriter(file);    //参数一定是File类型，可以有第二个参数，如果第二个参数为Ture，就是追加写入。
fw.write("一给我里giagiao！");
fw.write("1111222");
fw.flush();          //从缓冲区写入
fw.close();
```

- 文件读
```java
FileReader fr=new FileReader(file);
int len=0;
while((len=fr.read())!=-1){
	System.out.print((char)len);    //fr.read()每次读出一个ASC码，要转换成char
}
```

```java
FileReader fr=new FileReader(file);
char[] r=new char[200];
int len;
if ((len =read(r))!=-1)            //read(char[])将文件内容直接读入char数组中，返回的是占用的数组长度
	System.out.println(new String(r,0,len));  //String(r,0,len), char数组从0到len创建String
```

##  缓冲IO
- BufferWriter创建
```java
BufferedWriter bw=
new BufferedWriter(new(FileWriter(new File("file\\abc.txt"),true));
```
- 写入与文件写类似
- 新增方法newLine()
```java
BufferedWriter bw=new BufferedWriter(new FileWriter(new File("file\\abc.txt"),true));
bw.newLine();        //换行
bw.write("Ass We Can");
bw.close();
```
- BufferReader
```java
BufferedReader br=
new BufferedReader(new FileReader(new File("file\\\\abc.txt")));
```
- 新增方法readline()，每次直接读取一行
```java
String s=null;
while ((s=br.readLine())!=null) {   //注意，这里是不等于null
	System.out.println(s);
}
```

# 字节流 output/Input

## Fileoutputstream
```java
FileOutputSteam output=new FileOutputSteam(new File(""));
var s="Ass We Can";
output.writes(s.getBytes());
```
## Fileoutputstream
```java
input=new FileInputStream(new File("file/abc.txt"));
byte[] bs=new byte[10];
int len;
while ((len=input.read(bs))!=-1)
{
System.out.println(new String(bs,0,len));
}
```

## BufferOutputStream
```java
bos=new BufferedOutputStream(new FileOutputStream(new File("file/abc.txt")));
bos.write('A');
//并没有增加新的写入方法，只不过效率变高了。
```

# 字节流转字符流
- InputStreamReader
- OutputStreamWriter

# 序列化传输（可以传输对象）
- ObjectOutputStream
- ObjectInputStream
```java
oos=new ObjectOutputStream(new FileOutputStream(new File("file/stu.txt")));
oos.writeObject(s);
//注意，传输的对象要继承Serializable接口
```
```java
ois=new ObjectInputStream(new FileInputStream(new File("file/stu.txt")));
var s=ois.readObject();
System.out.println(s);
```
- 注意：写入两个对象在读的时候会有问题，因为写入的时候会写入头部标识符。写入两个对象会有两个标识符
   - 解决：继承ObjectOutputStream和 ObjectInputStream创建新的类，重写WriteHead方法
