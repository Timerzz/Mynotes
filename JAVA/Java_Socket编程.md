# InetAddress模块
- 通过InetAddress模块可以获得ip地址等信息
```java
System.out.println("本机信息："+ InetAddress.getLocalHost());
System.out.println("本机名字："+ InetAddress.getLocalHost().getHostName());
System.out.println("本机IP："+ InetAddress.getLocalHost().getHostAddress());
System.out.println("通过名称获得其他主机信息："+ InetAddress.getByName());
```
# DatagramSocket  UDP编程
- 通过DatagramSocket模块可以创建socket的客户端与服务器端
- 服务器端首先创建DatagramSocket实例，参数是接受数据的端口。而在客户端不需要参数
- 创建实例后通过receive接受数据，这里的数据要用DatagramPacket包裹，存放在byte数组中
- 服务器端
```java
  public static void main(String[] args) throws IOException {
        var sever = new DatagramSocket(8888);// 创建实例，参数为端口号
        while(true){   //循环接受
            byte[] b= new byte[1024];   //用byte数组接受数据
            sever.receive(new DatagramPacket(b,b.length));//接受数据
            System.out.println(new String(b));
        }
    }
```
- 客户端
```java
public static void main(String[] args) throws IOException {
        var client = new DatagramSocket();
        var str="Ass We Can";
        client.send(new DatagramPacket(str.getBytes(),str.length(), InetAddress.getLocalHost(),8888));
        System.out.println("用户端发送成功");
    }
```

# Socket TCP编程
- TCP编程分别用ServerSocket和Socket创建服务器端和用户端
- 创建服务器端的时候要传入端口地址
- 通过accept（）方法接收，接收的是一个Socket对象。Socket对象通过getInputStream方法可以获得一个输入流，通过对输入流操作可以读取信息
- 服务器端
```java
   var server = new ServerSocket(8888);

    var acp = server.accept();
    var input=acp.getInputStream();
            
    byte[] con=new byte[1024];
    int len;
    while((len=input.read(con))!=-1){
        System.out.println(new String(con,0,len));
    }
```

- 用户端
- 用户端用Socket建立，建立的时候，除了端口号还需要IP
- 通过client.getOutputStream.write方法可以发送消息，发送完要关闭
```java
var client = new Socket("192.168.60.9",8888);
client.getOutputStream().write("Ass We Can".getBytes());
client.close();
```

- 用户端也能接受，服务器端也能发送
    - 因为服务器端通过accept方法得到的是socket对象，socket对象就是用来创建客户端的对象，是可以发送的
    - socket对象也可以接受
 - 接受后发送的客户端
```java
var server = new ServerSocket(8888);

var acp = server.accept();  //获得socket对象
var input=acp.getInputStream();//获得soket对象的输入流，可以用来接受
var output=acp.getOutputStream();//获得socket对象的输出流，可以用来发送
byte[] con=new byte[1024];
int len;
while((len=input.read(con))!=-1){
    System.out.println(new String(con,0,len));
    output.write(con);  //发送
}

```

- 发送并接受的客户端
```java
var client = new Socket("127.0.0.1",8888);
client.getOutputStream().write("Ass We Can".getBytes());
System.out.println("已发送");

var in = client.getInputStream();
byte[] con=new byte[1024];
int len;
while ((len=in.read(con))!=-1)
    System.out.println(new String(con,0,len));
           
```

