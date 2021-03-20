<template>
  <li>
    <a href="#" class="member-box">
        <span class="member-name">{{name}}</span>
        <span class="margin-right" :style="'color:' + value.color">{{value.amount}}</span>
        <span class="vertical-line"> </span>           
        <span class="font">
          <img :class="'margin-caret arrow-'+ delta.color" :src="`${publicPath}caret-down.svg`">
          {{delta.amount}}
        </span>
    </a>
    <ul v-if="isParent && children.length > 0">
      <tree 
        v-for="(item,index) in children" 
        :children="item.children" 
        :name="item.name"
        :value="item.value"
        :delta="item.delta"
        v-bind:key="index"
      />
    </ul>
  </li>
</template>

<script>
export default { 
    props: [ 'name', 'value','delta','children' ],
    name: 'tree',
    computed:{
      isParent(){
        return this.children &&
        this.children.length
      }
    },
    data () {
      return {
        publicPath: process.env.BASE_URL
      }
    }
  }
</script>

