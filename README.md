@[toc]

#### 背景
```
目前公司Java项目集成使用Swagger插件自动生成接口文档；依赖此文档完成接口测试。
```
#### 需求
```
做接口测试时，需要组装请求接口url及参数，无限制的cp/cv；如何才能减去反复的手工活动？
推荐接口测试工具：JMeter/httprunner，不排除其他框架，往着DDT的方向考虑。
原理：都是模拟客户端向服务端发起请求，然后校验接口返回数据的过程。
```
#### 实现一
```
python编写脚本对swagger接口文档返回的josn数据对象进行解析，提取接口关键信息，按规则写入excel组成测试用例，结合jmeter完成自动化测试；
```
#### 实现二
```
引入大疆httprunner框架，生成的json格式的数据文件<亦可通过charles抓包工具导出har文件，再通过har2case转换json测试用例>，可以直接通过CLI执行；
```
#### 实现三
```
既然已知接口文档并且能解析数据形成excel或者json格式的测试用例，那么也可以结合python/java等开发语言集合单元测试框架搭建自动化测试框架。
```
#### 项目结构说明：
- logs存放脚本执行日志
- properties存放配置信息
- swagger存放json测试用例文件
- swaggerLib脚本
- utils工具包：实现json、excel、log、config的封装及使用
- config.py为项目路径的拼接
