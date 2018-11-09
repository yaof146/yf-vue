<template>
  <div class="rightContainer" father-component="App">
    <!--<foodItem v-bind:data="rightContainerData"/>-->
    <div class="content">
      <h3># <span>{{containerTitle}}</span></h3>
      <ul class="ul" v-for="containerItem in rightContainerData" v-bind:key="containerItem.containerId" v-if="containerId == containerItem.containerId">
        <li v-for="item in containerItem.containerList" v-bind:key="item.id">
            <div class="item-img">
                <img :src="item.img">
            </div>
            <div class="word">
                <div class="item-title">
                    <h4>{{item.title}}</h4>
                </div>
                <div class="item-sales">
                    <span>月销量：{{item.sales}}</span>
                </div>
                <div class="item-price">
                    <span class="price">￥{{item.money}}</span>
                    <span class="unit">/份</span>
                </div>
            </div>
            <div class="add">
                <i @click="reduceNum(containerId,item.id,containerItem)" class="iconfont icon-jiajian-1" v-if="item.number>0"></i>
                <span class="num" v-if="item.number>0">{{item.number}}</span>
                <i @click="addNum(containerId,item.id,containerItem)" class="iconfont icon-jiajian-"></i>
            </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'rightContainer',
  props:{
    containerId:{
      type:Number,
      require:true
    },
    containerTitle:{
      type:String,
      require:true
    }
  },
  methods:{
    // 加减法
    reduceNum:function(containerId,itemId,containerItem){
      var data = this.rightContainerData;
      for(let i in data){
        if(data[i].containerId==containerId){
          for(let y in data[i].containerList){
            var dataItem = this.rightContainerData[i].containerList[y];
            if(dataItem.id==itemId){
              if(dataItem.number>0){
                dataItem.number--;
              }
            }
          }
          
        }
      }
    this.changeCount(containerItem);
    },
  addNum:function(containerId,itemId,containerItem){
      var data = this.rightContainerData;
      for(let i in data){
        if(data[i].containerId==containerId){
          for(let y in data[i].containerList){
            var dataItem = this.rightContainerData[i].containerList[y];
            if(dataItem.id==itemId){
                dataItem.number++;

            }
          }
          
        }
      }
      this.changeCount(containerItem);
    },
    changeCount:function(containerItem){
      var menuTip = 0;
      var carTip = 0;
      var menuId = 0;
      var allPrice = 0;
      menuId = containerItem.containerId;

      var pageDataList = containerItem.containerList;
      for(var i in pageDataList){
        menuTip+=pageDataList[i].number;
      }

      var allData = this.rightContainerData;
      for(var y in allData){
        for(var x in allData[y].containerList){
          
          carTip+=allData[y].containerList[x].number;

          allPrice+=(allData[y].containerList[x].money)*(allData[y].containerList[x].number);
        }
      }
      console.log('btn click',containerItem)
      this.$emit('childAdd',menuId,menuTip,carTip,allPrice);
    }
  },
  data () {
    return {
        rightContainerData: [
          {
            containerId:11,
            containerList:[
              {id:1,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0,zero:'false'},
            ]
          },
          {
            containerId:22,
            containerList:[
              {id:1,img:require('../assets/0.jpg'),title:'卡布奇诺',sales:'37',money:15, number:0,zero:'false'},
              {id:2,img:require('../assets/0.jpg'),title:'摩卡咖啡',sales:'37',money:15, number:0,zero:'false'},
            ]
          },
          {
            containerId:33,
            containerList:[
              {id:1,img:require('../assets/0.jpg'),title:'芒果汁',sales:'37',money:15, number:0},
              {id:2,img:require('../assets/0.jpg'),title:'冰红茶',sales:'37',money:15, number:0},
              {id:6,img:require('../assets/0.jpg'),title:'西瓜汁',sales:'37',money:15, number:0},
            ]
          },
          {
            containerId:44,
            containerList:[
              {id:1,img:require('../assets/0.jpg'),title:'茶叶蛋',sales:'37',money:15, number:0},
              {id:2,img:require('../assets/0.jpg'),title:'椰子土司',sales:'37',money:15, number:0},
              {id:3,img:require('../assets/0.jpg'),title:'脉动',sales:'37',money:15, number:0},
              {id:4,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
            ]
          },
          {
            containerId:55,
            containerList:[
              {id:1,img:require('../assets/0.jpg'),title:'美式咖啡',sales:'37',money:15, number:0},
              {id:2,img:require('../assets/0.jpg'),title:'意式浓缩',sales:'37',money:15, number:0},
              {id:3,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
              {id:4,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
              {id:5,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
            ]
          },
          {
            containerId:66,
            containerList:[
              {id:1,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
              {id:2,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
              {id:3,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
              {id:4,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
              {id:5,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
              {id:6,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
              {id:7,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
              {id:8,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
              {id:9,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
              {id:10,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
              {id:11,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
              {id:12,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
              {id:13,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
              {id:14,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
              {id:15,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
              {id:16,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
              {id:17,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
              {id:18,img:require('../assets/0.jpg'),title:'拿铁',sales:'37',money:15, number:0},
            ]
          },

            
            
        ],
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
 .rightContainer{
   flex-grow:1;
   overflow-y:hidden;
 }
 .rightContainer .content{
    font-size:14px;
    height: 100%;
    display:flex;
    flex-direction:column;
}
.rightContainer .content h3{
    text-align:left;
    font-size:14px;
    font-weight:normal;
    margin:0;
    padding:15px 10px 10px;
    border-bottom:1px solid #ccc;
}
.rightContainer .ul{
  padding-left:10px;
  flex-grow:1;
  overflow-y:auto;
}
.rightContainer ul li{
    display:flex;
    padding:10px 0 5px;
    border-bottom:1px solid #eee;
}
.item-title h4{
    font-size:13px;
    margin:0;
}
.item-sales{
    flex-grow:1;
}
.item-sales span{
    font-size:8px;
    -webkit-text-size-adjust:none;
}
.item-price .price{
    color:#ff0000;
    font-weight:600;
    font-family:微软雅黑;
    line-height: 10px;
    font-size:14px;
}
.item-price .unit{
    color:#70da70;
    font-size:7px;
    font-weight:400;
    line-height:7px;
    -webkit-text-size-adjust:none;
}
.rightContainer .item-img{
    margin-right:10px;
    width:55px;
    height:55px;
}
.rightContainer .item-img img{
    width:100%;
    height:100%;
}
.rightContainer ul li div.word{
    width:80px;
    display:flex;
    flex-grow:1;
    flex-direction:column;
    align-items:flex-start;
}
.rightContainer ul li div.add{
    display: flex;
    align-items: center;
    margin-right:10px;
}
.rightContainer ul li div.add i{
    width:18px;
    height:18px;
    border-radius:50%;
    color:#e4b220;
    font-size:10px;
    line-height:18px;
    text-align:center;
    border:1px solid #333;

}
.add .num{
  padding:0 5px;
}
</style>
