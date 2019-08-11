##  三种等待方式
1. 显式等待
显示等待是等待具体的元素加载
```python

from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait                            # available since 2.4.0
from selenium.webdriver.support import expected_conditions as EC           # available since 2.26.0
driver = webdriver.Firefox()
driver.get("http://somedomain/url_that_delays_loading")
try:
    element = WebDriverWait(driver, 10).until(EC.presence_of_element_located((By.ID, "myDynamicElement")))
finally:
```

2. 隐士等待
这种事等待整格页面的加载
```python

driver = webdriver.Firefox()
driver.implicitly_wait(10)                      # seconds
driver.get(http://www.xxx.com)

```
