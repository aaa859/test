<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <link rel="stylesheet" href="./index.css">
    <script src="./vue.js"></script>
</head>

<div id="app" >
    <div class="goods" v-for = '(goods ,goodsindex) in goodsList' :key = 'goods.id'>
        <div class="title">{{goods.title}}:</div>
        <ul class="type-list">
            <!-- 加active的判断逻辑为数组默认的的index是不是当前行内元素的index  通过点击赋值 -->
            <!-- goods.index goods因为为每个对象，对象包含一个属性为数组，因为是数组，所以数组里面默认有index  typeindex当前行下面中的每一项的index为定义的typeindex-->
            <li class = 'type' :class = '{active:goods.index === typeindex}' 
            v-for = '(type,typeindex) in goods.typeList' @click = handleClick(typeindex,goods,type,goodsindex)>{{type}}</li>
            <li >{{goods.index}}</li>
        </ul>
    </div>
    <div class="choose-type">
        <div>已选条件：</div>
        <span class="no-goods" v-if = '!panduan'>暂时没有选择过滤条件</span>
        <ul v-else class="filter-list">
            <li  v-for = 'item  in newType' >{{item}}</li>
        </ul>
    </div>
</div>
<body>
    <script>// created || mounted(){     
        // }
        
        // vue实例加载完了之后，通过ajax，请求后端数据，给data赋值
        
        const vm = new Vue({
            data:{
                panduan:false,
                goodsList: [
          {
            title: '上装',
            typeList: ['全部', '针织衫', '毛呢外套', 'T恤', '羽绒服', '棉衣', '卫衣', '风衣' ],
            id: 1,
          },
          {
            title: '裤装',
            typeList: ['全部', '牛仔裤', '小脚/铅笔裤', '休闲裤' ,'打底裤', '哈伦裤'],
            id: 2,
          },
          {
            title: '裙装',
            typeList: ['全部', '连衣裙', '半身裙', '长袖连衣裙', '中长款连衣裙'],
            id: 3,
          },
        ],
        newType :{}
            },
            methods:{
                handleClick(typeindex,goods,type,goodsindex){
                    // 将当前行具有active的样式改为行里面单个元素具有active样式
                    goods.index = typeindex
                    console.log(typeindex)
                    vm.$set(this.newType,goodsindex,type)
                    this.panduan = true;
                }
            },
            el:'#app'
        }) 
        vm.goodsList.forEach((item)=> vm.$set(item,'index',0))
        // console.log(vm.goodsList)
        //goodsList的每个对象加index属性
        // vm.goodsList.forEach((item)=> item.index = 0)
        // console.log(vm.goodsList)
        </script>
</body>
</html>
