# JFast - API
## 一、简单说明
- 本函数库将JQuery原型进行了替换，添加了本函数库的原型，使得本函数库的方法能够直接通过JQuery来调用，使用方便，符合目前javaScript主流
- 本函数库基于JQuery，并在JQuery的基础上添加了新的特性，使得开发者能够更加快捷地实现功能的开发
- 本函数库属于JQuery的扩展函数库，本函数库的诞生是为了针对页面功能的实现便捷性
- 所有方法都能通过jf.来调用，部分方法能够直接使用JQuery选择器来调用
## 二、API
#### 1. typeAll(objs,index)方法

尝试返回一个对象的类型，也可以是一个html组件

- 参数
  + objs 用来获取类型的对象
  + index 下标（可选），从1开始，用来获取第几个元素的类型，默认为1

- 使用格式
  + 直接选取html组件作为传入对象
  ```js
  $("#f_html").typeAll();
  ```

  + 自定义传入对象
  ```js
  var objes = {
	  'name':'张三',
	  'age':'李四'
  }
  jf.typeAll(objs);
  ```

  + 如果对象有多个，可以传入下标值来表明获取第几个对象的类型
  ```js
  $(".f_html").typeAll(index);
  ```
#### 2. typeArray(objs)方法

以数组的方式返回多个对象的类型

- 参数
  
+ objs 多个对象的数组
  
- 使用格式
  + 选取html作为传入对象
  ```js
  $(".f_html").typeArray();
  ```
  + 自定义传入对象
  ```js
  var objes = {
  	  'name':'张三',
  	  'age':'李四'
  }
  jf.typeArray(objs);
  ```

#### 3. getStringPair(str)方法

以对象的方式返回字符串中所有的键值对

- 参数
  
+ str 包含键值对的字符串
  
- 键值对的形式
  + key(或'key'或"key")='val'(或"val")
  + key(或'key'或"key"):'val'(或"val")

- 使用格式
  ```js
  var str = "这里是干扰,name:'jFast'这里是干扰,ver='1.0.0'这里是干扰";
  jf.getStringPair(str); //返回结果：["name:'jFast'", "ver='1.0.0'"]
  ```

#### 4. inputRegAlert(sor,iden,alertInfo)方法

验证输入框内容是否符合规则，符合不显示或去除提示返回true，否则显示提示信息返回false

- 参数
  + sor 选中的输入框
  + iden 内容规则（正则或规则关键字），关键字详情请见testReg()方法
  + alertInfo（可选） 提示信息，默认为格式错误

- 使用格式
  ```js
  $("#phone").inputRegAlert("phone","手机号格式错误");
  ```

#### 5. inputAlert(sor,condition,alertInfo)方法

接收一个Boolean条件值，如果为false在选中元素后提示信息，否则不显示或去除信息

- 参数
  + sor 选中的输入框
  + condition Boolean条件值
  + alertInfo（可选） 提示信息，默认为“格式错误”

- 使用格式
  ```js
  $("#phone").inputAlert(true,"手机格式错误");
  ```

#### 6. checkInputValueAlert(sor,value,alertInfo)方法

判断输入框中的值是否与传入的值相同，不同则在选中元素后提示信息

- 参数
  + sor 选中的输入框
  + value 要匹配的内容
  + alertInfo（可选） 提示信息，默认为“两个值不同”

- 使用格式
  ```js
  $("#password").checkInputValueAlert("123","密码错误！");
  ```

#### 7. testReg(str,iden)方法

验证一段字符串是否符合正则表达式或规则，符合返回true，否则返回false

- 参数
  + str 需要验证的字符串
  + iden 正则表达式或规则关键字

- 内置的规则关键字
  + phone 手机号码格式，/^1[34578]\d{9}$/
  + name 中文姓名格式，/^[\u4E00-\u9FA5]{1,6}$/
  + ID 身份证号格式，/(^\d{15}$)|(^\d{18}$)|(^\d{17}(\d|X|x)$)/
  + username 账号格式，/^[a-zA-Z0-9_-]{4,16}$/
  + password 密码格式，/^(_|\w+|\d+){6,15}$/
  + passwordStrong 严格密码格式（至少各包含大小写数字特殊字符），/^.*(?=.{6,})(?=.*\d)(?=.*[A-Z])(?=.*[a-z])(?=.*[!@#$%^&*? ]).*$/
  + email 邮箱格式，/^([A-Za-z0-9_\-\.])+\@([A-Za-z0-9_\-\.])+\.([A-Za-z]{2,4})$/


- 使用格式
  ```js
  var phone = 1370665743;
  jf.testReg(phone,"phone"); //返回结果：true
  ```

#### 8. repx(str)方法

返回“12px”格式字符串中数字的浮点类型

- 参数
  
+ str 字符串
  
- 使用格式
  ```js
  jf.repx("12px"); //返回结果：12
  ```
  
#### 9. stringRepxNum(str)方法

如果字符串为空返回0，否则返回第一串数字的浮点类型

- 参数
  
+ str 字符串
  
- 使用格式
  ```js
  jf.stringRepxNum("fdkjnk324"); //返回结果：324
  jf.stringRepxNum(); // 返回结果：0
  ```
  
#### 10. getStringNumArray(str)方法

返回字符串中数字串组成的数组

- 参数
  
+ str 字符串
  
- 使用格式
  ```js
  jf.getStringNumArray("sdf12dgef34"); //返回结果：["12","34"]
  ```
  
#### 11. getElemMatrixArray(sor)方法

返回选中元素的2d矩阵数组

- 参数
  
+ sor 选中的元素
  
- 使用格式
  ```js
  $("div").getElemMatrixArray();
  ```
  
#### 12. getElemMarginArr(sor)方法

回元素的margin数值数组

- 参数
  
+ sor 选中元素
  
- 使用格式
  ```js
  $("div").getElemMarginArr();
  ```

- 结果格式
  ```js
  [0,0,0,0,]
  ```
  
#### 13. getElemDeviation(sor)方法

返回元素的偏移距离，包括margin与translate所发生的元素偏移

- 参数
  
+ sor 选中元素
  
- 使用格式
  ```js
  $("div").getElemDeviation();
  ```
  
- 结果格式 
  ```js
  {devTop:0,devLeft:0}
  ```

#### 14. mouseBlockMove(sor)方法

使元素能够通过鼠标移动

- 参数
  
+ sor选中元素
  
- 需要添加的class
  
+ f\_head 如果选中元素下含有class="f\_head"的子元素，则鼠标只能通过该子元素移动选中的整个元素
  
- 使用格式
  ```js
  $("div").mouseBlockMove();
  ```
  
#### 15. PreviewPhoto(sor,preimg,scale)方法

大图预览商品图效果

- 参数
  + sor 选中元素
  + preimg 预览图地址
  + scale（可选） 放大倍数（1.5-5），超出范围按默认倍数2

- 需要添加的class
  + f\_preview 要预览图片的元素，该元素大小建议不要小于原图所在元素
  + f\_slider 原图中的滑块，该滑块大小根据预览图自行调节

- 使用格式
  ```js
  $("div").PreviewPhoto("img/p1.jpg",3);
  ```
