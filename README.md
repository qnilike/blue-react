#react:
###好在哪里：
	1.组件化---分工、合作；
	2.虚拟DOM---性能高；
	3.跨平台---移动端；
###缺点：
	1.学习过程比较陡；
	2.设计思想有点特别；
###react全家桶（技术栈）
	1.react主体
	2.webpack：grunt、gulp自动化构建工具
	3.flex：布局
	4.react的route：路由。
	5.redux：帮助来做view层
	6.Mocha：做测试的
	7.Istanbul：覆盖率
###jsx：
	1.对js语法的一种增强，html代码可以直接放在js里边，
	2.babel：用来编译jsx的
	注意：
		有且只有一个父级元素
###最强悍的地方
	1.组件
	2.状态
####举例 indexPAge---组件
	<header>
	</header>
		<contet>
		</contet>
	<footer>
	</footer>
	1.定义组件--组件--class	
		class 名称 extends React.Component{
			render(){
				return 内容
			}
		}
	2.使用组件
		就跟用标签一样，
		ReactDOM.render(
			<span>111</span>,
			oDiv
		)
		ReactDOM.render(
			<Comp/>,
			oDiv
		)
####状态
	属性(props)---定死的
	状态(state)---变的
	1.constructor里边--this.state={value:'abc'},初始化
	2.函数里边--this.setState({value：""}),设置state。
	3.事件大小写
		onChange
		onClick
		onChange={this.fn.bind(this)}
		
	4.render 返回的元素加className而不是class
	5.用constructor的时候，必须用super
### sd
	1.angular霸道--原声定时器、jq
	2.react--温柔
### 生存周期
	componentWillMount() 即将创建完成
	componentDidMount()  创建完成之后

	componentWillUpdate() 更新之前
	componentDidUpdate()  更新之后

	componentWillUnmount() 销毁之前
	没有componentDidUnmount()，已经销毁没有事件啦

	componentWillReceiveProps()组件参数更新

### 创建列表的问题
	1.直接操作arr是不能点击修改li的，react是状态机，得操作state才能实时更新。
	2.列表2使用了state设置之后，会出现一个关于key的警告，react会根据这个key来对比DOM元素之间的差距来进行更新。
###写内部style样式
	1.style={{color:this.state.color}},固定死的写法
###关于DOM的操作ref
	1.在组件标签上设置ref=“string”，在组件事件中通过this.refs.string取值，这样就可以取到组件中的元素。
	2.在constructor中取不到，因为组件还没有挂载。
###表单
	1.用value设置默认值，会导致表无法输入，改成defaultValue
	2.checkbox是否默认选中，同上，不用checked，得用defaultChecked=“true”
###事件冒泡
	1.传统的js使用stopPropagation或者cancelBubble，两者区别：前者不支持ie，符合w3c;后者支持ie，不符合w3c.
	//ev.cancelBubble=true;不可取
	//ev.stopPropagation();不可取
	2.stopPropagation不可取的原因是，react将事件委托给了document，并不是不能阻止，而是等他阻止的时候事件已经传递给了document。
	（3）.可以解决的ev.nativeEvent.stopImmediatePropagation();
###组件间的通信
	1.父级有个a，要在子级中访问到？
	答：父级给子级传值用属性，子级访问这个属性用props；demo:父子组件通信.html
	2.子级向父级传值？
	答：类似于回调函数一样，demo:子级向父级加值.html
###为什么用webpack
	1.babel实时编译，慢
	2.测试，麻烦
	3.自己搭建服务器
	4.没有热更新
###webpack
	1.配置webpack
		安装webpack--cnpm install -g webpack  #webpack的cli环境
	    cnpm install -g webpack-dev-server   #webpack自带的服务器
	2.各种包的依赖安装
		cnpm init     #创建packjson
		cnpm install babel-core -D  #后台编译babel工具
		cnpm install babel-preset-es2015 -D  #babel对es5的预设
		cnpm install babel-loader -D   #babel的加载器
	注意：
		-D等同于--save-dev，加入到项目中去
	3.webpack本身
		cnpm install webpack -D   #webpack本地依赖库
		cnpm install webpack-dev-save -D #webpack服务器的本地依赖
		cnpm install babel-preset-react -D   #babel-react的预设

		cnpm install react -D   #react本身
		cnpm install react-dom -D  #react-dom本身
	
		cnpm install react-hot-loader -D  #热更新过
		
		cnpm install style-loader -D
		cnpm install css-loader -D
	4.webpack的配置文件
		webpack.config.js    #webpack的配置文件
		.baberc   #babel预设文件
	5.webpack-dev-server:实时更新，cmd运行这个；cmd运行webpack就是打包一下，不是实时

