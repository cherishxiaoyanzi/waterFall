<template>
  <div class="water-fall_wrap" id="water-fall">
      <div class="water-fall_content" v-for="(item,index) in items" :key="index">
          <img :src="item.url"/>
          <p>teettett</p>
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
        items:[
            {url:require('../assets/1.jpg')},
            {url:require('../assets/2.jpg')},
            {url:require('../assets/3.jpg')},
            {url:require('../assets/4.jpg')},
            {url:require('../assets/5.jpg')},
            {url:require('../assets/6.jpg')},
            {url:require('../assets/7.png')},
            {url:require('../assets/8.jpeg')},
            {url:require('../assets/9.png')},
            {url:require('../assets/10.png')},
            {url:require('../assets/11.png')},
            {url:require('../assets/12.png')}
        ]
    };
  },
  methods: {

  },
  mounted(){
      window.onload=()=>{
            let imgHArr=[];
            let imgs=document.getElementById('water-fall').children;
            let len=imgs.length;
          for(let i=0;i<len;i++){
                  let height=imgs[i].clientHeight;
                    if(i<3){
                        imgHArr.push(height);
                        imgs[i].style.left=i*403+"px";
                    }else{
                        var minheight=Math.min.apply(null,imgHArr);
                        var minIndex=imgHArr.findIndex((value)=>{

                            return value == minheight
                        });
                        if(minIndex>=0){
                            imgs[i].style.top=(imgHArr[minIndex] +10)+ "px";
                            imgs[i].style.left=minIndex*403+"px";
                        }
                            imgHArr[minIndex] = minheight+imgs[i].clientHeight + 10
                        
                        
                    }
          
            }
      }
      
    
      
      
  }
};
</script>

<style scoped>
    .water-fall_wrap{
        width: 1200px;
        height: 100%;
    }
    .water-fall_wrap img{
        display: inline-block;
        width:393px;
        margin-right: 10px;
        position: absolute;
        left: 0;
        top: 0;
    }
    .water-fall_wrap img:nth-child(3n){
        margin-right: 0;
    }
</style>
