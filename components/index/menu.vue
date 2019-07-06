<template>
  <div class="m-menu">
    <dl
      class="nav"
      @mouseleave="mouseLeave"
    >
      <dt>全部分类</dt>
      <dd
        v-for="(item,idx) of menu"
        :key="idx"
        @mouseenter="mouseEnter"
      >
        <i :class="item.type" />{{ item.title }}<span class="arrow" />
      </dd>
    </dl>
    <div
      v-if="kind"
      class="detail"
      @mouseenter="cMouseEnter"
      @mouseleave="cMouseLeave"
    >
      <template v-for="(item,idx) of curDetailData.detail"> 
        <h4 :key="idx">
          {{ item.title }}
        </h4>
        <span
          v-for="child of item.child"
          :key="child"
        >{{ child }}</span> 
      </template>
    </div>
  </div>
</template>

<script>
  export default{
    data(){
      return {
        kind:'',
        menu:[{
          type:'food',
          title:'美食',
          detail:[{
            title:"美食",
            child:['火锅','烧烤','']
          }]
        },{
          type:'takeout',
          title:'外卖',
          detail:[{
            title:"外卖",
            child:['火锅','烧烤','']
          }]
        },{
          type:'hotel',
          title:'酒店',
          detail:[{
            title:"酒店",
            child:['火锅','烧烤','']
          }]
        }]
      }
    },
    computed:{
      curDetailData(){
        return this.menu.filter((item)=>{return item.type === this.kind})[0]
      }
    },
    methods:{
      mouseEnter(e){
        this.kind = e.target.querySelector('i').className;
      },
      mouseLeave(){
        this._timer = setTimeout(() => {
          this.kind = ''
        }, 150);
      },
      cMouseEnter(){
        clearTimeout(this._timer)
      },
      cMouseLeave(){
        this.kind = '' 
      }
    }
  }
</script>

<style lang="scss">

</style>