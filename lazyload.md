# lazyload

#### 模版方式模式

```
//实现的基本骨架
var defaultConfig = {//默认的基础配置
    
}

function popup(content, config){
    var cf = $.extend(true, {}, defaultConfig, config);
    //.....
    var method = {//popup默认函数

        show: function() {},

        hide: function() {},

        fadeOut: function() {},

        remove: function() {}

    };

    return method;
}

popup.loading = function(config){
    config = $.extend(true, {}, {
        //..
    }, config);
    return popup(content,config)
}
popup.note = function(text,config){
    config = $.extend(true, {}, {
        //..
    }, config);
    return popup(content,config)
}
```


### 不用继承的方式实现模板模式
```
//好莱坞原则
//子类放弃对自己的控制权，由父类通知子类该何时调用何种方法
var Beverage = function(param) {

	var boilwater = function() {
		console.log('把水煮沸')
	}

	var brew = param.brew || function() {
		throw new Error('brew 方法不能为空')
	}

	var pourInCup = param.pourInCup || function() {
		throw new Error('pourInCup 方法不能为空')
	}

	var addCondiments = param.addCondiments || function() {
		throw new Error('pourInCup 方法不能为空')
	}

	var F = function(){}

	F.prototype.init = function(){
		boilwater()
		brew()
		pourInCup()
		addCondiments()
	}

	return F

}

var Coffee = Beverage({
	brew: function(){
		console.log('用沸水冲泡咖啡')
	},
	pourInCup: function(){
		console.log('把咖啡倒进杯子')
	},
	addCondiments: function(){
		console.log('加糖和牛奶')
	}
})

var Tea = function(){
	brew: function(){
		console.log('用沸水浸泡茶叶')
	},
	pourInCup: function(){
		console.log('把茶倒进杯子')
	},
	addCondiments: function(){
		console.log('加柠檬')
	}
}

var coffee = new Coffee()
coffee.init()

var tea = new Tea()
tea.init()
```


