<template>
  <div class="hello">
    <div class="start_content" v-show="start">
            <button @click="startGame">{{startValues}}</button>
    </div>
     <div class="main_content">
                <ul>
                       <li class="item_box" v-for="item in items" >
                              <p>{{item}}</p>
                       </li>
                </ul>
     </div>
     <div class="btn_content" >
          <btn v-show="items.length>1"  @over="stopGame" @go="goGame" ref="btn"></btn>
     </div>
  </div>
</template>

<script>
import btn from './btn'
import data from '../data'
export default {
  name: 'hello',
  data () {
    return {
        items:  [],
        start: true,
        startValues: 'start',
        time: 0,
        talk : data.talk
    }
  },
  components: {
    btn
  },
  methods: {
    startGame() {
      this.start= false
      this.items.push('！！！能看到吗！')
      setTimeout(() => {
        this.items.push('能看到的话请告诉我！')
      }, 1000)
    },
    stopGame(value) {
      this.start= true
      this.startValues=value
      this.items= []
    },
    goGame() {
      this.time++
      for (let i=0; i<this.talk.length; i++) {
        if (this.time === this.talk[i].time) {
          console.log(this.talk[i].btn1, this.talk[i].btn2)
          this.$refs.btn.opOne=this.talk[i].btn1
          this.$refs.btn.opTwo=this.talk[i].btn2
          this.items.push(this.talk[i].item)
        }
      }
    }
  }
}
</script>
<style >
.main_content{
  width:100%;
  height: 90%;
  background: rgb(43, 45, 66);
  position: absolute;
  top:0;
  left:0;
  overflow: scroll;
}
.btn_content{
  width:100%;
  height:10%;
  background: rgb(0, 52, 89);
  position: absolute;
  bottom:0;
  left:0;
}
.item_box{
  list-style: none;
  width:90%;
  min-height: 60px;
  margin:5% auto 3% auto;
  border:1px solid rgba(141, 153, 174, 0.8);
  border-radius: 15px;
  background: rgba(43, 45, 66,0.8);
}
.item_box>p{
  font-size: "微软雅黑";
  font-weight: 0;
  color:rgb(141, 153, 174);
  font-size: 20px;
  text-align: left;
  width:95%;
  margin:20px auto;
}
.start_content{
  width:100%;
  height: 100%;
  background: #fff;
  position: absolute;
  top:0;
  left:0;
  z-index:10;
}
.start_content>button{
  margin:70% 0;
  border:none;
  background: #fff;
  outline:none;
}
</style>
