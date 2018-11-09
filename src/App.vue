<template>
  <div id="app">
    <div class="top">
      <leftMenu @childChangeContainer="changeContainer" :leftMenuData="leftMenuData"/>
      <rightContainer @childAdd="add" :containerId="showContainerId" :containerTitle="showContainerTitle"/>
    </div>
    <div class="bottom">
      <bottomContainer @childAdd="add" :carTip="showCarTip" :allPrice="showAllPrice"/>
    </div>
  </div>
</template>

<script>
// 
    // 
import leftMenu from './components/leftMenu'
import rightContainer from './components/rightContainer'
import bottomContainer from './components/bottomContainer'
export default {
  name: 'App',
  components:{leftMenu,rightContainer,bottomContainer},
  data(){
    return {
      showContainerId:11,
      showContainerTitle:'咖啡',
      showCarTip:0,
      showAllPrice:0,
      leftMenuData: [
            {id:11,iconfontClass:'icon-kafei',txt:'咖啡',num:0},
            {id:22,iconfontClass:'icon-yinliao',txt:'饮料',num:0},
            {id:33,iconfontClass:'icon-mianbao',txt:'面包',num:0},
            {id:44,iconfontClass:'icon-taocan',txt:'套餐',num:0},
            {id:55,iconfontClass:'icon-tubiaozhizuomoban-',txt:'西餐',num:0},
            {id:66,iconfontClass:'icon-hongjiu',txt:'红酒',num:0},
      ],
    }
  },
  methods:{
    changeContainer:function(item){
      console.log('item.id',item.id);
      this.showContainerId = item.id;
      this.showContainerTitle = item.txt;
    },
    add:function(menuId,menuTip,carTip,allPrice){
      var leftMenuData=this.leftMenuData;
      for(var z in leftMenuData){
        if(leftMenuData[z].id==menuId){
          leftMenuData[z].num=menuTip;
          console.log('nnnnnnnnn',this.leftMenuData[z].num)
        }
      } 
      this.showCarTip=carTip;
      this.showAllPrice=allPrice;
    }
  },

}
</script>

<style>
html,body{
   font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0px;
  padding:0;
  width:100%;
  height:100%;
  -webkit-text-size-adjust:none; 
}
#app {
  height:100%;
  display:flex;
  flex-direction:column;
  overflow:hidden;
}
.top{
  display:flex;
  flex-direction:row;
  flex-grow:1;
}
.bottom{
  display:fixed;
  bottom:0;
  left:0;
  width:100%;
  background:#fff;
  align-self:flex-end;

}
ul{
    padding:0;
    margin:0;
}
img{
    width:45px;
    height:45px;

}
li{
  list-style:none;
}



@font-face {font-family: "iconfont";
  src: url('//at.alicdn.com/t/font_908903_hkj0mfm0n4o.eot?t=1541690201117'); /* IE9*/
  src: url('//at.alicdn.com/t/font_908903_hkj0mfm0n4o.eot?t=1541690201117#iefix') format('embedded-opentype'), /* IE6-IE8 */
  url('data:application/x-font-woff;charset=utf-8;base64,d09GRgABAAAAAAt8AAsAAAAAEPgAAQAAAAAAAAAAAAAAAAAAAAAAAAAAAABHU1VCAAABCAAAADMAAABCsP6z7U9TLzIAAAE8AAAARAAAAFY8dkqPY21hcAAAAYAAAAChAAACLh6SIXRnbHlmAAACJAAABv8AAAmoBZ9o/2hlYWQAAAkkAAAALgAAADYTNyyvaGhlYQAACVQAAAAeAAAAJAfhA5hobXR4AAAJdAAAABMAAAAsLAwAAGxvY2EAAAmIAAAAGAAAABgMVA4wbWF4cAAACaAAAAAeAAAAIAEgALpuYW1lAAAJwAAAAUUAAAJtPlT+fXBvc3QAAAsIAAAAcQAAAJfeC/HgeJxjYGRgYOBikGPQYWB0cfMJYeBgYGGAAJAMY05meiJQDMoDyrGAaQ4gZoOIAgCKIwNPAHicY2BkYWScwMDKwMHUyXSGgYGhH0IzvmYwYuRgYGBiYGVmwAoC0lxTGByeMbyYw9zwv4EhhrmBoQEozAiSAwDpNAyCeJzlks0NwjAMRp/pD6TqgQPi0hVQB+mly9AdGKIHTozmdotix5ygG+DoRfGnJI6+GKiAwrgZJcgLweNpqmS9oMl6yd3yC2dTShVN2mqng446Lf06bxsoe+pPiN1y/RpYFaHmxJHEwaoV/japd87/W7R5fnyyxn0O8loC/y1NgfmItoE5inaBeYsOAb53DMxvdAq8C5Y+8M5Y54DqDXNZMy8AAAB4nK1WXWzb1hW+516Sl5RESiQlkbIsShQl0o5d2ZItym5iyXbjJR0Sb4kdoy7QJRvaZVsCZHkogqEJamQBhr0E22B0BYoBwwosxZohRQv0pdiwbg/DBrhYtyd7P8ayYtvTihUosBQ2s0MpC9y+bA8jyMtz7v3OIXl+vksiEHJ/QyBsgySJRRbIaUJAIjxPrJB0fMJ8EqCAqkRAg5wDlodXTgPLDf2g3YVOsxP2WNijYacdtqf9gLsIaEAwHXZQymV9SrajXUkCd3sbXEmKdre3ovdFEfStLdBFMXo/elZWYHEGhBkhcUWGQL6eQNFMJZMqzSQlWWZUkYeiP0uH3HAJmABdgQHbiD0d8LznHXC5hY+g9woXhz91oQj18tFSTVVrpaPlOiRkJaEKRk7N2gVQtdLFwmbzsqOfW9Sf0PEU84RQjMm77A6b6MeEmPgZWYm7DZgOQe9CK2/pGlT9q0w2bNvY+xeOcBGsmgX94UcPxWjlAISgN3J/h32PjRJCOJFJmmTQf4t0yafJl8gGIaKXzYfTvtT5xJ1jODHSLSvfBT/wPQ04xniqS31zIOJiA9gAhaoG0KDVNCaMZ/MWTjhQgmz+MLTCTtjWWVYKPH8OGuANTKY7rTLkLVopxse1/ni5P+7deIUJv3px7YSiJyR57Quvviewn74gyCpLja1covTSymo8rvbOAJzpza9SOAPrCVPVeSLsgpmVNA5iOV/Ui6I4wVhRAhmKVYCml2QCY4KUzmTK6bSUSafLmYwz0GasX3zju78WRgTJ0MVx4S+3X/zjECQNjQYPn7dyKXqFrs73VildjR87leAUqPntS0vztmwZULDvWU5WVy36+/26kQAQ71XdWf9z559FGQ+GKSAQD+wOvBFnxnRb+azkuVV/OvxYZl+3PRtPhIqYv6/jWz9PqmQJM/YS+TE60WjVDzsYRewHDCfKoQNSGiQuDUJv/VeE+D8ggGNz4etJPJe34qR2LHcqzmcnnANsvLCV5xoEGua5P+3zLJdwJq7bAItmDlx4R5lUjRTwpCvSVCqRFfhhzo0k47KiWBJV5bT1kowQlfJEdQARJYToScoVOWFxmlI0K/qJ3By4qQoslUr23cgfx9CzhXE9pex9qKQAqqXm+GOCCEcF4WRr1h2hk8d80f7WISWVUuZey9Ajb3rDzWBeid5W2pUxu0x36ZX6TCKtS8poTs+lEsPZhZNMpDghy5pXT2YUdbTyf0DcAz1zKoGf+Y+nT3bH68MAQ7Wx7smnDwuCNznpXX6KQspQrz0XHn97/bF2vWRTWigG7aUnt4mEtfBXdp6NkxQpEIeMYB8vYhU5MOW2wgeZ6sbKg6qyPJ6bauJ6vwvNusswN3H/QQwPvDjbDoQ9+CFgpa+rpqHt39KMAIIyXXdGRpz9W87IFWk4OMZKxkdGiR3b/ztdWhZb7kduU4LbcjIp39GEIlXSKrXpOc0wi4apouWRkRHqipFjFAoG3PX3P6iMAYxV6O+SOjaD9jVsZln+8sN++BO9ScZQwSqTBtXoVT3roSbxgehjqfG8UKkh89DbM7ZQcAUtDA49YujSwpBQqIjao6Ph9NwQQ7HQO/sVYCDAbUDqfpleO31Ot5TMo+fHBfmJC7qdyBy58IiknfliPPvMqfr19Zs3btz86ncIifenn9MP2WF8pxVygTwfs2QD2jpeZszFJci3ejQu/xxyWKvT7wQLmYfrSHNT+jS2VZv5VZ6LObs9AX41TWMxaOMkQ37M5+CBxwmkxB50wUISzT0w98fAj3OTn4o7EbHfXxC5U1UgY2eoQKmQKWTwmwSKOihVh88GfKisgAgxAjcrEddiETkIlPIQh6unRERwhtYs/VRBVk3+eAdpJXM6zYAC46WC2AUuws/0xVFIYyK1u7K8vKmZRnpzWZbvoqBF/xxd1KN5kdvwliykZmugKQqumNrypixvLscSWkUf1GZTghyNx/5mrVZaAn9h7dWLSIGmtvcmmrOuILCzP1iZ9aXMRFbAuiYH/wkKxCcThOj/+SEIJFLHDUnqM1AbmYpJuC92BzwHJhJOGfQpXQR3Zwdc3Ip3d3aiXfrCua2jC+ZnVt5dbRri1UqngufkPKXzt5zhhNmcgA1EiQessjPB2pO/OfE4Pf63tfJS9BaUO90ZB+hCs7kA33RKJ7y16Le0QZDI77/D/oB7dYa45LOE1FsOzSKfNuh0l4oHFbMVcyqNSdFzLbeV6zdmgwbMwxHrBjvTwdfPlyk8Y1YKmlao+OX4VoaXjaqtaXa15sY3942ikwLcApNSKihGsgbvNYxipJhDRoKtHU+bqjCU/7xpqUg4VBCva3alPjCsV2yNfkJ1tbwt154rm76zFmSL+nAlDb/UslbCLCQNRedaqUb+DTc8gQAAeJxjYGRgYADiSJY88Xh+m68M3CwMIHCDqyQSQf9vYGFmbgByORiYQKIA3DEIBAAAeJxjYGRgYG7438AQw8LDAAQszAyMDKiAGwBIdgKDAAB4nGNhYGBgQcc8WMSAGAAFYAA5AAAAAAAAigC2AX4BlgKcAwYDUAQKBGAE1HicY2BkYGDgZlgHxCDABMRcQMjA8B/MZwAAG24B2wAAeJxlj01OwzAQhV/6B6QSqqhgh+QFYgEo/RGrblhUavdddN+mTpsqiSPHrdQDcB6OwAk4AtyAO/BIJ5s2lsffvHljTwDc4Acejt8t95E9XDI7cg0XuBeuU38QbpBfhJto41W4Rf1N2MczpsJtdGF5g9e4YvaEd2EPHXwI13CNT+E69S/hBvlbuIk7/Aq30PHqwj7mXle4jUcv9sdWL5xeqeVBxaHJIpM5v4KZXu+Sha3S6pxrW8QmU4OgX0lTnWlb3VPs10PnIhVZk6oJqzpJjMqt2erQBRvn8lGvF4kehCblWGP+tsYCjnEFhSUOjDFCGGSIyujoO1Vm9K+xQ8Jee1Y9zed0WxTU/3OFAQL0z1xTurLSeTpPgT1fG1J1dCtuy56UNJFezUkSskJe1rZUQuoBNmVXjhF6XNGJPyhnSP8ACVpuyAAAAHicbYvBDoJADEQ7KHQBT/6HBz6pS5AtyvZCQ+Tr3YR482UubzJDFZ109J8eFS64okYDRkCLDj1uxMnyvKiHRaUkP5pNbJTc/nyoX/KclD+a3yrGaymj2H3zWPRIeritFsuSz+cQZvPdxzQRfQFZoSGkAAAA') format('woff'),
  url('//at.alicdn.com/t/font_908903_hkj0mfm0n4o.ttf?t=1541690201117') format('truetype'), /* chrome, firefox, opera, Safari, Android, iOS 4.2+*/
  url('//at.alicdn.com/t/font_908903_hkj0mfm0n4o.svg?t=1541690201117#iconfont') format('svg'); /* iOS 4.1- */
}

.iconfont {
  font-family:"iconfont" !important;
  font-size:16px;
  font-style:normal;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.icon-hongjiu:before { content: "\e601"; }

.icon-jiajian-:before { content: "\e64f"; }

.icon-taocan:before { content: "\e72e"; }

.icon-jiajian-1:before { content: "\e675"; }

.icon-kafei:before { content: "\e89c"; }

.icon-yinliao:before { content: "\e609"; }

.icon-mianbao:before { content: "\e61b"; }

.icon-tubiaozhizuomoban-:before { content: "\e60c"; }

.icon-taocan1:before { content: "\e64a"; }

.icon-gouwuche:before { content: "\e600"; }

</style>
