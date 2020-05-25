1.
   输出结果：10
   原因：var声明的i,在全局范围内有效，所以数组a中的i指向的是同一个i，所以输出的值都是最后一轮循环的值，也就是10

2.
  输出结果： 无法在初始化之前使用 tmp;
  原因：let不存在变量提升，因为let的注册和初始化是解耦的

3.
  var arr=[12,32,34,89,4]
  var minNum=Math.min(...arr)
  解析：利用Math.min()方法求最小值，但是该方法的参数是一个数值列表，所以需要把数组展开后传入该方法

4.

使用var声明的变量，其作用域为该语句所在的函数内，且存在变量提升现象；（注册和初始化阶段是不解耦的）
使用let声明的变量，其作用域为该语句所在的代码块内，不存在变量提升；（注册和初始化阶段是解耦的）
使用const声明的是常量，得在声明的时候就赋值（注册和初始化阶段是解耦的）
----如果该常量是基本类型，则在后面的代码中不能再修改该常量的值
----如果该常量是引用类型，则在后面的代码中不能改变该常量的映射地址，但是可以改变该常量的属性值

5.
 输出结果：20
 原因：因为setTimeout()会在全局对象上被调用，所以this指向全局对象，但是此处setTimeout()是剪头函数，剪头函数是没有this机制的，所以它的this始终指向当前作用域。此处的调用者是obj,所以this指向obj对象，输出结果为20

6.
 ----表示一个独一无二的值
 ----模拟对象的私有成员
 最主要的作业就是为对象添加独一无二的属性名

7.
 浅拷贝----只复制指向某个对象的指针，而不复制对象本身，新旧对象还是共享同一块内存
    ---实现方法
     ----简单的赋值
     ----slice()方法
     ----Object.assign()实现（当对象只有一层时是深拷贝，当对象是多层时是浅拷贝）

 深拷贝----会另外创造一个一模一样的对象，新对象跟原对象不共享内存，修改新对象不会改到原对象。
      ----Object.assign()实现（当对象只有一层时是深拷贝，当对象是多层时是浅拷贝）
      ----转成 JSON 再转回来---JSON.parse(JSON.stringify(obj));

8.
   异步编程：程序无须按照代码顺序自上而下的执行，不会等待这个任务结束才开始下一个任务
   ----回调函数
   ----事件监听
   ----发布/订阅模式
   ----promise
   ----Generator(ES6)
   ----async/await(ES7)

   Event loop ----事件循环机制,负责监听调用栈和消息队列，当调用栈中所有的任务都结束了，事件循环就会从消息队列中取出第一个回调函数，压到调用栈中


   宏任务----每次执行栈执行的代码就是一个宏任务（包括每次从事件队列中获取一个事件回调并放到执行栈中执行）
        ----script
        ----setTimeout
        ----setInterval
        ----I/O
        ----UI交互事件
        ----postMessage
        ----MessageChannel
        ----setImmediate(Node.js环境)

    微任务----在当前 task 执行结束后立即执行的任务-----在当前task任务后，下一个task之前，在渲染之前
         +---在某一个macrotask执行完后，就会将在它执行期间产生的所有microtask都执行完毕（在渲染前）。
         ----Promise.then()
         ----Object.observe
         ----MutaionObserve
         ----process.nextTick(Node.js环境)


9.
   function setTime(val) {
		return new Promise(function(resolve, reject) {
            setTimeout(()=>{
                ry{
                  	resolve(val);
                }catch(e){
                  	reject(e);
                }
            },10)
		})
	}
			
	setTime("hello").then(function(res){
		let str=res+"lagou";
		return setTime(str);
	}).then(function(res){
		console.log(res+"I ❤ U");
	})


10.
   TypeScript是一门基于JavaScript之上的编程语言，是JavaScript的超集，解决了JavaScript自由类型系统的不足，大大提高代码的可靠程度。


JavaScript：
   ----JavaScript是一种基于客户端浏览器的，基于对象、事件驱动式的脚本语言（弱类型且动态类型）
   ----JavaScript使用的变量是弱类型
   ----JavaScript语言具有动态性。JavaScript是事件驱动的，只根据用户的操作做出相应的反应处理。
   ----JavaScript只依赖于浏览器，与操作系统的因素无关。因此JavaScript是一种跨平台的语言。

TypeScript：
   ----TypeScript是Microsoft推出的开源语言，使用Apache授权协议
   ----TypeScript增加了静态类型、类、模块、接口和类型注解
   ----TypeScript可用于开发大型的应用

JavaScript和TypeScript的主要差异
   ----TypeScript可以使用JavaScript中的所有代码和编程概念，TypeScript是为了使JavaScript的开发变得更加容易而创建的。

   ----TypeScript从核心语言方面和类概念方面的模塑方面对JavaScript对象模型进行扩展。
   ----JavaScript代码可以在无需任何修改的情况下与TypeScript一同工作，同时可以使用编译器将TypeScript代码转换为JavaScript。
   ----TypeScript通过类型注解提供编译时的静态类型检查。
   ----TypeScript中的数据要求带有明确的类型，JavaScript不要求。
   ----TypeScript提供了缺省参数值。
   ----TypeScript引入了JavaScript中没有的“类”概念。
   ----TypeScript中引入模块的概念，可以把声明、数据、函数和类封装在模块中。

TypeScript的优势
   ----静态类型化，允许开发人员编写更健壮的代码并对其进行维护。
   ----大型的开发项目，使用TypeScript工具来进行重构更容易、便捷。
   ----类型安全，在编码期间检测错误的功能，而不是在编译项目时检测错误。
   ----干净的ECMAScript6代码，自动完成和动态输入等因素有助于提高开发人员的工作效率。


JavaScript的优势
   ----JavaScript的开发者社区仍然巨大而活跃，在社区可以很容易找到大量成熟的开发项目和可用资源。
   ----JavaScript语言发展较早，也较为成熟。
   ----TypeScript代码需要被编译（成JavaScript）
   ----不需要注释
   ----JavaScript的灵活性更高


如何选择：
----在开发大型开发项目时，使用TypeScript更加合适。如果有一个相对较小的编码项目，似乎没有必要使用TypeScript，只需使用JavaScript。



11.
   TypeScript的优势
   ----静态类型化，允许开发人员编写更健壮的代码并对其进行维护。
   ----大型的开发项目，使用TypeScript工具来进行重构更容易、便捷。
   ----类型安全，在编码期间检测错误的功能，而不是在编译项目时检测错误。
   ----干净的ECMAScript6代码，自动完成和动态输入等因素有助于提高开发人员的工作效率。

   TypeScript的不足：
   ----有一定的学习成本
   ----对小型项目不太适合，增加开发成本
   ----目前还不太成熟，和一下库结合的不是很完美


