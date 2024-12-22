
### 5\.1\.4 自动生成测试数据


        测试数据的生成通常是接口测试的一个烦琐任务。ChatGPT可以帮助测试团队生成测试数据，包括各种输入和它们的组合。测试人员可以描述他们需要的数据类型和范围，ChatGPT可以生成符合要求的测试数据，从而减轻测试人员的负担。


　　对于一个在线预订酒店的用户登录接口的测试，需要输入用户名、密码、电话和电子邮箱信息。ChatGPT可以根据接口测试的需要生成多条不同测试数据，下面以生成10000条user表的数据为例。在ChatGPT中输入提示词，其就能给出Python代码，运行代码后就能得到SQL文件。ChatGPT生成的部分SQL文件如图5\-1所示。


 


![](https://img2024.cnblogs.com/blog/15184/202412/15184-20241221122355655-663757295.png)


图5\-1  ChatGPT生成的部分SQL文件


**ChatGPT****生成的完整的****SQL****文件**



```
   要生成10000条包含用户名、密码、邮箱和手机号的SQL插入语句，你可以使用Python编写脚本，然后执行它以生成SQL语句。以下是一个示例Python脚本，用于生成这些SQL语句：
```



```
import random

import string

 

# 生成符合长度要求的随机用户名

def generate_username(length):

    username = ''.join(random.choice(string.ascii_letters) for _ in range(length))

    return username

 

# 生成包含大小写字母、数字和特殊符号的随机密码

def generate_password(length):

    characters = string.ascii_letters + string.digits + string.punctuation

    password = ''.join(random.choice(characters) for _ in range(length))

    return password

 

# 生成格式正确的随机邮箱地址

def generate_email():

    username = generate_username(random.randint(5， 10))

    domain = ''.join(random.choice(string.ascii_lowercase) for _ in range(5))

    extension = random.choice(['com'， 'net'， 'org'])

    email = f"{username}@{domain}.{extension}"

    return email

 

# 生成符合手机号格式的随机数字

def generate_phone_number():

    area_code = random.randint(100， 999)

    exchange = random.randint(100， 999)

    subscriber_number = random.randint(1000， 9999)

    phone_number = f"({area_code}) {exchange}-{subscriber_number}"

    return phone_number

 

# 生成10000条SQL插入语句

sql_statements = []

for _ in range(10000):

    username = generate_username(8)

    password = generate_password(12)

    email = generate_email()

    phone_number = generate_phone_number()

   

    # 构建插入语句

    sql = f"INSERT INTO user (username， password， Email， phone) VALUES ('{username}'， '{password}'， '{email}'， '{phone_number}');"

    sql_statements.append(sql)

 

# 保存SQL语句到文件

with open("insert_data.sql"， "w") as file:

    for statement in sql_statements:

        file.write(statement + "\n")
```



```
此脚本将生成10000条SQL插入语句，将这些数据插入名为"user"的数据表中。你可以根据你的数据库类型和需求修改生成的SQL语句，确保它们与你的数据库架构相匹配。生成的SQL语句将保存在名为"insert_data.sql"的文本文件中。
```

### 5\.1\.5 更新和维护测试用例


　　随着系统的演化，测试用例需要不断更新和维护。ChatGPT可以用来协助测试人员，根据新的接口规范和需求来修改测试用例。这有助于确保测试用例始终与系统的最新版本保持一致。


在一个电子邮件应用程序的接口测试中，我们需要测试发送电子邮件的功能。随着新的电子邮件格式和附件要求的变化，我们需要更新测试用例以适应这些变化。ChatGPT可以帮助我们快速修改测试用例，以满足新的需求，从而减少维护测试用例的工作量。


### 5\.1\.6 自动生成接口测试代码


　　对于常用的接口测试工具或者测试框架，如Postman、JMeter、pytest等，ChatGPT都可以生成相应的接口测试用例脚本等。测试人员只需描述接口信息和测试场景，通常就可以获得可直接运行的接口测试用例脚本。


　　针对上例的购物车接口，ChatGPT生成的JMeter测试用例脚本，如下所示。


**ChatGPT****生成的****JMeter****测试用例脚本**




```
</spanxml version="1.0" encoding="UTF-8"?>

<jmeterTestPlan version="1.2" properties="5.0" jmeter="5.5">

  <hashTree>

    <TestPlan guiclass="TestPlanGui" testclass="TestPlan" testname="测试计划">

      <stringProp name="TestPlan.comments">stringProp>

      <boolProp name="TestPlan.functional_mode">falseboolProp>

      <boolProp name="TestPlan.tearDown_on_shutdown">trueboolProp>

      <boolProp name="TestPlan.serialize_threadgroups">falseboolProp>

      <elementProp name="TestPlan.user_defined_variables"

elementType="Arguments" guiclass="ArgumentsPanel"

testclass="Arguments" testname="用户定义的变量" enabled="true">

        <collectionProp name="Arguments.arguments"/>

      elementProp>

      <stringProp name="TestPlan.user_define_classpath">stringProp>

    TestPlan>

    <hashTree>

      <ThreadGroup guiclass="ThreadGroupGui" testclass="ThreadGroup"

testname="线程组">

        <stringProp name="ThreadGroup.on_sample_error">continuestringProp>

        <elementProp name="ThreadGroup.main_controller"

elementType="LoopController" guiclass="LoopControlPanel"

testclass="LoopController" testname="循环控制器" enabled="true">

          <boolProp name="LoopController.continue_forever">falseboolProp>

          <stringProp name="LoopController.loops">1stringProp>

        elementProp>

        <stringProp name="ThreadGroup.num_threads">1stringProp>

        <stringProp name="ThreadGroup.ramp_time">1stringProp>

        <boolProp name="ThreadGroup.scheduler">falseboolProp>

        <stringProp name="ThreadGroup.duration">stringProp>

        <stringProp name="ThreadGroup.delay">stringProp>

        <boolProp

name="ThreadGroup.same_user_on_next_iteration">trueboolProp>

      ThreadGroup>

      <hashTree>

        <HTTPSamplerProxy guiclass="HttpTestSampleGui"

testclass="HTTPSamplerProxy" testname="HTTP请求" enabled="true">

          <elementProp name="HTTPsampler.Arguments" elementType="Arguments"

guiclass="HTTPArgumentsPanel" testclass="Arguments"

testname="用户定义的变量" enabled="true">

            <collectionProp name="Arguments.arguments">

              <elementProp name="item_id" elementType="HTTPArgument">

                <boolProp name="HTTPArgument.always_encode">falseboolProp>

                <stringProp name="Argument.value">123456stringProp>

                <stringProp name="Argument.metadata">=stringProp>

                <boolProp name="HTTPArgument.use_equals">trueboolProp>

                <stringProp name="Argument.name">item_idstringProp>

              elementProp>

              <elementProp name="num" elementType="HTTPArgument">

                <boolProp name="HTTPArgument.always_encode">falseboolProp>

                <stringProp name="Argument.value">1stringProp>

                <stringProp name="Argument.metadata">=stringProp>

                <boolProp name="HTTPArgument.use_equals">trueboolProp>

                <stringProp name="Argument.name">numstringProp>

              elementProp>

            collectionProp>

          elementProp>

          <stringProp name="HTTPSampler.domain">www.example.comstringProp>

          <stringProp name="HTTPSampler.port">stringProp>

          <stringProp name="HTTPSampler.protocol">httpstringProp>

          <stringProp name="HTTPSampler.contentEncoding">stringProp>

          <stringProp name="HTTPSampler.path">/cart/addstringProp>

          <stringProp name="HTTPSampler.method">POSTstringProp>

          <boolProp name="HTTPSampler.follow_redirects">trueboolProp>

          <boolProp name="HTTPSampler.auto_redirects">falseboolProp>

          <boolProp name="HTTPSampler.use_keepalive">trueboolProp>

          <boolProp name="HTTPSampler.DO_MULTIPART_POST">falseboolProp>

          <stringProp name="HTTPSampler.embedded_url_re">stringProp>

          <stringProp name="HTTPSampler.connect_timeout">stringProp>

          <stringProp name="HTTPSampler.response_timeout">stringProp>

        HTTPSamplerProxy>

        <hashTree>

          <ResponseAssertion guiclass="AssertionGui"

testclass="ResponseAssertion" testname="响应断言" enabled="true">

            <collectionProp name="Asserion.test_strings">

              <stringProp name="49586">200stringProp>

            collectionProp>

            <stringProp name="Assertion.custom_message">stringProp>

            <stringProp

name="Assertion.test_field">Assertion.response_codestringProp>

            <boolProp name="Assertion.assume_success">falseboolProp>

            <intProp name="Assertion.test_type">8intProp>

          ResponseAssertion>

          <hashTree/>

        hashTree>

      hashTree>

    hashTree>

  hashTree>

jmeterTestPlan>
```


### 5\.1\.7 智能对比新旧接口


　　在接口迭代升级的过程中，往往需要修改对应的接口测试用例。ChatGPT可以通过对比新旧接口规范，智能生成修改接口测试用例的建议。


　　例如，购物车接口进行了变更，新旧接口文档示例如下所示。


**新旧接口文档示例**




```
原接口:

接口:add_to_cart

方法:POST 

参数:item_id， num

......

新接口:

接口:add_to_cart

方法:POST

参数:item_id， num， selected

......
```


 


　　ChatGPT可以快速指出新接口文档中添加了selected参数，并给出更新测试用例的建议。ChatGPT给出的更新测试用例的建议如下所示。


**ChatGPT****给出的更新测试用例的建议**



> \- 新接口在原有基础上新增了selected参数，需要在原有用例中补充该参数的测试。
> 
> 
> \- selected参数可以传入0或1，表示状态是否选中。需要新增用例验证该参数的逻辑。
> 
> 
> \- 需要保留原有不传selected参数的兼容性用例。


　　这样可以避免测试人员逐一手动对比了解接口的变更，从而大幅提升修改接口测试用例的效率。


 
 本博客参考[wgetCloud机场](https://tabijibiyori.org)。转载请注明出处！
