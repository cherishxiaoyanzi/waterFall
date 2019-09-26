<template>
  <div class="water-fall_wrap" id="water-fall" ref="waterScroll">
      <div class="water-fall_content" v-for="(item,index) in items" :key="index">
          <img class="water_img" :src="item.url" v-if="item.url"/>
          <p>{{item.text}}</p>
      </div>
      
      <!-- <img src="../assets/2.jpg"/>
      <img src="../assets/3.jpg"/>
      <img src="../assets/4.jpg"/>
      <img src="../assets/5.jpg"/>
      <img src="../assets/6.jpg"/>
      <img src="../assets/7.png"/>
      <img src="../assets/8.jpeg"/>
      <img src="../assets/9.png"/>
      <img src="../assets/10.png"/>
      <img src="../assets/11.png"/>
      <img src="../assets/12.png"/> -->
  </div>
</template>

<script>
export default {
  name: '',
  data() {
    return {
        minheight:0,
        waterTop:0,
        isReload:false,
        items:[
            // {url:require('../assets/1.jpg'),text:"pic1"},
            // {url:require('../assets/2.jpg'),text:"pic2"},
            // {url:require('../assets/3.jpg'),text:"pic3"},
            // {url:require('../assets/4.jpg'),text:"pic4"},
            // {url:require('../assets/5.jpg'),text:"pic5"},
            // {url:require('../assets/6.jpg'),text:"pic6"},
            // {url:require('../assets/7.png'),text:"pic7"},
            // {url:require('../assets/8.jpeg'),text:"pic8"},
            // {url:require('../assets/9.png'),text:"pic9"},
            // {url:require('../assets/10.png'),text:"pic10"},
            // {url:require('../assets/11.png'),text:"pic11"},
            // {url:require('../assets/12.png'),text:"pic12"},
        ],
        // items:[
        //     {text:'更改了声优聊天  青年音  语音313S  更改为了萝莉音更改了声优聊天  青年音  语音313S  更改为了萝莉音更改了声优聊天  青年音  语音313S  更改为了萝莉音更改了声优聊天  青年音  语音313S  更改为了萝莉音'},
        //     {text:'更改了声优聊天  青年音  语音313S  更改为了萝莉音'},
        //     {text:'更改了声优聊天  青年音  语音31'},
        //     {text:'兴趣爱好：大萨达撒大声地 阿达的方法是否阿大多数 阿达萨达是兴趣爱好：大萨达撒大声地 阿达的方法是否阿大多数 阿达萨达是兴趣爱好：大萨达撒大声地 阿达的方法是否阿大多数 阿达萨达是兴趣爱好：大萨达撒大声地 阿达的方法是否阿大多数 阿达萨达是'},
        //     {text:'兴趣爱好：大萨达撒大声地 阿达的方法是否阿大多数 阿达萨达是兴趣爱好：大萨达撒大声地 阿达的方法是否阿大多数 阿达萨达是'},
        //     {text:'更改了声优聊天  青年音  语音313S  更改为了萝莉音更改了声优聊天  青年音  语音313S  更改为了萝莉音更改了声优聊天  青年音  语音313S  更改为了萝莉音更改了声优聊天  青年音  语音313S  更改为了萝莉音'},
        //     {text:'更改了声优聊天  青年音  语音313S  更改为了萝莉音'},
        //     {text:'兴趣爱好：大萨达撒大声地 阿达的方法是否阿大多数 阿达萨达是兴趣爱好：大萨达撒大声地 阿达的方法是否阿大多数 阿达萨达是兴趣爱好：大萨达撒大声地 阿达的方法是否阿大多数 阿达萨达是兴趣爱好：大萨达撒大声地 阿达的方法是否阿大多数 阿达萨达是'},
        //     {text:'更改了声优聊天  青年音  语音31'},
        //     {text:'兴趣爱好：大萨达撒大声地 阿达的方法是否阿大多数 阿达萨达是兴趣爱好：大萨达撒大声地 阿达的方法是否阿大多数 阿达萨达是'}
        // ]
    };
  },
  props:{
      waterWrapWidth:{
          type:Number,
          default:0,
      },
      blockWidth:{
          type:Number,
          default:0,
      },
      gap:{
          type:Number,
          default:0,
      },
      wrapList:{
          type:Array,
          default(){
              return []
          }
      }
  },
  methods: {
      waterScroll(){
          if(this.isReload){return}
              var waterScroll=this.$refs.waterScroll;
          this.waterTop = document.documentElement.scrollTop || document.body.scrollTop;
          console.log("document.documentElement",document.documentElement.offsetHeight,this.minheight)
          if(this.waterTop + document.documentElement.offsetHeight-500 > this.minheight){
              this.isReload=true;
              this.items.push(
                  {url:require('../assets/1.jpg'),text:"pic1"},
                  {url:require('../assets/4.jpg'),text:"pic4"},
                    {url:require('../assets/5.jpg'),text:"pic5"},
                    {url:require('../assets/6.jpg'),text:"pic6"},
                    {url:require('../assets/7.png'),text:"pic7"}
                  );
            this.$nextTick(()=>{
                
                    this.preLoad()
                
                
            })
          }
          
      },
      preLoad(){
          let imgs=document.getElementsByClassName('water_img');
            let imgsL = document.getElementsByClassName('water_img').length;
            let promiseAll = [], img = [];
            for(let i=0;i<imgsL;i++){
                promiseAll[i] = new Promise((resolve, reject)=>{
                    img[i] = new Image()
                    img[i].src = imgs[i].src;
                    img[i].onload = function(){
                        //第i张加载完成
                        resolve(img[i])
                    }
                })
            }
            Promise.all(promiseAll).then((img)=>{
                //全部加载完成
                this.getDom();
                this.waterFall();
                this.isReload=false
            })
      },
    waterFall(){
        let childHArr=[];
            let children=document.getElementById('water-fall').children;
            let len=children.length;
          for(let i=0;i<len;i++){

                  let height=children[i].clientHeight;
                    if(i<3){
                        childHArr.push(height);
                        children[i].style.left=i*(this.blockWidth+this.gap)+"px";
                    }else{
                        this.minheight=Math.min.apply(null,childHArr);
                        var minIndex=childHArr.findIndex((value)=>{
                            return value == this.minheight
                        });
                        if(minIndex>=0){
                            children[i].style.top=(childHArr[minIndex] +this.gap)+ "px";
                            children[i].style.left=minIndex*(this.blockWidth+this.gap)+"px";
                        }
                            childHArr[minIndex] = this.minheight+children[i].clientHeight + this.gap
                        
                        
                    }
          
            }
    },
    getDom(){
        document.getElementById('water-fall').style.width=this.waterWrapWidth+"px";
       let children=document.getElementById('water-fall').children;
        let len=children.length;
        for(let i=0;i<len;i++){
            children[i].style.width=this.blockWidth+"px";
            children[i].style.marginRight=this.gap+'px';
            let j=(2+3*i);
            // children[j].style.marginRight='0px';

        }
    }
  },
//   watch:{
//       waterTop(val){
//           this.$refs.waterScroll.addEventListener('scroll',this.waterScroll())
//       }
//   },
  mounted(){
      this.scrollTop=0;
      this.items = this.wrapList;
      this.getDom();
    this.$nextTick(()=>{
        this.preLoad();
    })
      
    //   window.onload=()=>{
    //     this.waterFall();
            
    //   }
      window.addEventListener('scroll',this.waterScroll)
    
      
      
  }
};
</script>

<style scoped>
    .water-fall_wrap{
        width: 1200px;
        height: 970px;
    }
    .water-fall_wrap .water-fall_content{
        display: inline-block;
        width:393px;
        margin-right: 10px;
        position: absolute;
        left: 0;
        top: 0;
        border: 1px solid #f00;
        transition: all .1s linear;
    }
    .water-fall_content img{
        width: 100%;
    }
    .water-fall_wrap .water-fall_content:nth-child(3n){
        margin-right: 0;
    }
</style>
