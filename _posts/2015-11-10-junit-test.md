---
layout: post
title:  "单元测试"
date:   2015-11-10 10:15:35 +0800
categories: [java,单元测试]
---

##单元测试的好处

1. 提高测试覆盖率
2. 为重构提供保证
3. 作为示例和文档
4. 减少DEBUG
5. 对比Main
	- 可以单个、多个、全部运行
	- 运行结果直观
	- 不会污染业务类

##junit简介
- `JUnit4`
- `org.junit`
- `@Test`
- `@Before,@After`
- `@BeforeClass`,`@AfterClass`
- 每个测试用例必须独立，不能有依赖
- 每个测试用例必须有结果验证(assertXXX)

##junit注意事项

1. 功能测试，如果类依赖其它类。尽量通过`mock`来模拟依赖的组件。这样才准确的定位出错的地放。如果依赖组件需要另一成员来开发，也不会出问题。`mock`可以使用第三放jar包如：`easyMock` `jmock` 等
2. 测试参与了数据存储或修改必须进行还原操作，以免影响测试库。
3. 现在的web层很多项目都分成三层 `dao` `service` `controler`,针对这几层的测试，`dao`需要遵循第2原则。`service`层最好通过`Mock dao`来解决依赖。`controller`中不能处理业务逻辑，主要处理参与与显示，因此可以不用进行测试。
4. 业务类和测试类所在的包需要相同，这样对`protected`方法与`省略`方法进行测试。
5. 现在web项目基本都用到了`spring`，`spring`带来了很大的方便。特别是在依赖注入方面。可以通过`attribute` `construct` `set`等进行注入。虽然减少了代码量，但通过`attribute`注入，并且如果没有set方法或提供`construct`初始化。导致此类相当于被强引用，对单元测试与脱离`spring`容器都带来了一定的麻烦。在注入时最好是通过`construct`方式。
6. 提高测试的覆盖率，如边界条件、分支、多条件等。
7. 多通过TDD(测试驱动开发来)进行测试。这样可以让写出的代码出bug机率减少。