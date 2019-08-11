# 重定向
- 重定向的使用场景：
    - 主要是一些进行跳转的界面
    - 比如，进行进入主界面的时候，没有登录，自动跳转到登录界面

- 重定向的方法：
    使用redirect方法
```python
def index(request):
    username = request.GET.get('username')
    if username:
        return HttpResponse("{}的首页".format(username))
    else:
        return  redirect('/login/')  #重定向，注意，需要return
```

# url命名与转换
- 为什么要url命名与转换
    - 如果后面进行修改，那么要改动的地方就比较多，所有的相关的重定向都要修改。而且容易有错误
- url命名方法
    - 在path方法中有name属性，可以直接设置name的值，作为命名
    ```python
    path('login/',views.login,name='signin'),
    path('',views.index,name='index')
    ```
- url反转
    - 给url命名后，如何使用？
    - 重定向的时候用reverse方法，将url的名字反转成路径
    ```python
    # 导入reverse方法
    from django.shortcuts import  redirect,reverse
    ...
       return  redirect(reverse('login'))
    ```
# 命名空间
- 在多个app中有可能会给不同的urls相同的name，这个时候重定向就无法正确的反转
- 解决办法：给每一个app的urls.py起一个app_name作为应用命名空间
```python
# 在urls.py中
app_name='cms' #这个app的应用命名空间为cms
```
```python
# 在重定向的name前面加上应用命名空间：
return  redirect(reverse('cms:login'))
```