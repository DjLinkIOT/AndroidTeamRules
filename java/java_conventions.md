# 格式规范

## 文档排版规范

- 文档层面的结构包括：`括号风格`, `缩进`, `列限制`, `换行`, `空格`, `空行`

## 具体结构规范

- 具体结构包括：`枚举`, `变量`, `数组`, `switch`, `注解`, `注释`, `修饰符`

## CodeStyle 配置

- 统一用 [Android Studio CodeStyle 配置](https://djlinkiot.github.io/2016/11/26/android-studio-code-style-check-style/) 来规范所有格式

## 注意事项

- 使用快捷键进行代码格式自动化：
  - Windows：`CTRL + ALT + L`
  - Mac：`OPTION + COMMAND + L`

- 范围型的常量用枚举类定义，而不要直接用整型或字符，这样可以减少范围值的有效性检查

# 命名规范

## 包名

- 包名全部小写

- 公司（或个人）项目的域名倒序，“.”分隔，单个包名建议不超过12个字母。

    例如，google的gson项目，包名为 `com.google.gson`

- 连续的单词只是简单地连接起来，不使用下划线

- 在部门内部应该规划好包名的范围，防止产生冲突。部门内部产品使用部门的名称加上模块名称。产品线的产品使用产品的名称加上模块的名称。

  - 格式：
    ```Java
    com.公司名.产品名.模块名称
    com.公司名.部门名称.项目名称
    ```
  - 实例：
    ```Java
    com.djlink.iot.sdk  //djlink iot部门 SDK项目
    com.djlink.cloud.order //djlink 云平台产品 预约模块
    ```

## 类名

- 首字母大写的驼峰式（ `UpperCamelCase` ）风格命名

- 类名通常是名词或名词短语，意义完整的英文描述

### 测试类

- 以它要测试的类的名称开始，以Test结束。

- 例如，`HashTest` 或 `HashIntegrationTest`

### 管理类

- 文件管理、设备管理、用户管理这种具有管理某一类事物的功能的类

- 建议规则：语义名词 + “Manager”

- 示例： 文件管理：FileManager 设备管理：DeviceManager 用户管理：UserManager

### 工具类

- 处理一些特定场景问题的类

- 建议规则：场景名词/动词 + Util

- 示例： 下载工具类：DownloadUtil 日期工具类：DateUtil 字符串处理工具类：StringUtil

## 接口名

- 接口名称有时可能是形容词或形容词短语

    例如 `Runnable`， `Cloneable`

- 如果语义不是很清晰，尽量用I开头，避免产生歧义

### 回调接口

- 其命名规则：`On + 名称 + Callback`

### 监听接口（观察者模式）

- 其命名规则：`On + 名称 + Listener` 或者 `名称 + Observer`

## 方法名

- 首字母小写的驼峰式（ `UpperCamelCase` ）风格命名



## 常量名

- 都以UpperCamelCase（驼峰式）风格命名
- 类名通常是名词或名词短语
- 测试类的命名：以它要测试的类的名称开始，以Test结束。例如，HashTest或HashIntegrationTest

## 非常常量名

- 都以UpperCamelCase（驼峰式）风格命名
- 类名通常是名词或名词短语
- 测试类的命名：以它要测试的类的名称开始，以Test结束。例如，HashTest或HashIntegrationTest

## 

# 注释规范

## 规则

- 注释量：一般情况，源程序有效注释量必须在`20%`左右
- 注释原则：有助于对程序理解，语言必须准确、易懂、简洁

## 包的注释

- 写入一个名为 `package.html` 的说明网页放入当前路径，方便 `JavaDoc` 收集
- 注释内容：简述本包作用（整个项目中的位置）、详细描述本包的内容、产品模块名称和版本、公司版权
- 格式：

    ```html
    <html>
        <body>
            <p>一句话描述
            <p>详细描述
            <p>产品模块名称和版本
            <br>公司版权信息
        </body>
    </html>
    ```

- 示例：com/djlink/iot/sdk/cmd/package.html

    ```html
    <html>
        <body>
            <p>SDK中发送指令功能类，上层业务使用本包与设备发指令
            <p>采用xxx设计思路
            <p>MMSC v1.2.1
            <br>(C) 版权所有 200x-200y 北京鼎甲微联科技有限公司
        </body>
    </html>
    ```

## 文件注释

- 注释位置：写入文件头部，包名之前的位置

- 注意以 `/*` 开始避免变 `JavaDoc` 收集

    ```Java
    /*
     *  注释内容
     */

    package com.djlink.iot.sdk.cmd;
    ```
- 文件注释内容：描述信息、创建日期、创建人、修改日期、修改人、版权说明 (可选)

    ```Java
    /*
     *  版权：Copyright xxx. All Rights Reserved.
     *  描述：<描述该文件功能>
     *  创建人：<修改人名 邮箱>
     *  创建时间：yyyy-MM-dd
     *  修改人：<修改人名 邮箱>
     *  修改时间：yyyy-MM-dd
     *  修改内容：<修改内容>
     */
    ```
    每次修改后在文件头部写明修改信息。
    ```Java
    /*
     *  版权：Copyright xxx. All Rights Reserved.
     *  描述：<描述该文件功能>
     *  创建人：<修改人名 邮箱>
     *  创建时间：yyyy-MM-dd
     *  修改人：<修改人名x 邮箱>
     *  修改时间：yyyy-MM-dd
     *  修改内容：<修改内容x>
     *  修改人：<修改人名y 邮箱>
     *  修改时间：yyyy-MM-dd
     *  修改内容：<修改内容y>
     */
    ```

## 类和接口的注释

- 注释位置：该注释放在 `package` 关键字之后，`class` 或者 `interface` 关键字之前。方便 `JavaDoc` 收集。

    ```Java
    package com.djlink.iot.sdk.cmd;

    /*
     *  注释内容
     */
    public class CommandManager
    ```

- 注释内容：类的注释主要是一句话功能简述、功能详细描述


## 成员变量的注释

## 成员方法的注释

## 代码中的注释


# 编码规范

## 