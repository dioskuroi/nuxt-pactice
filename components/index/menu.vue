<template>
  <div class="m-menu">
    <dl class="nav" @mouseleave="mouseLeave">
      <dt>全部分类</dt>
      <dd v-for="({ type, name }, index) in menu" :key="index" @mouseenter="enter">
        <i :class="type">{{ name }}</i>
      </dd>
    </dl>
    <div v-if="kind" class="detail" @mouseenter="sover" @mouseleave="sout">
      <template v-for="({ title, child }, index) in currDetail">
        <h4 :key="index">
          {{ title }}
        </h4>
        <span v-for="(v, i) in child" :key="'s' + i">{{ v }}</span>
      </template>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      kind: '',
      menu: [{
        type: 'food',
        name: '美食',
        child: [{
          title: '美食',
          child: ['代金券', '甜点饮料', '火锅', '自助餐', '小吃快餐']
        }]
      }, {
        type: 'takeout',
        name: '外卖',
        child: [{
          title: '外卖',
          child: ['美团外卖']
        }]
      }]
    }
  },
  computed: {
    currDetail () {
      return this.menu.find(item => item.type === this.kind).child
    }

  },
  methods: {
    mouseLeave () {
      this._timer = setTimeout(() => {
        this.kind = ''
      }, 150)
    },
    enter ({ target }) {
      this.kind = target.querySelector('i').className
    },
    sover () {
      clearTimeout(this._timer)
    },
    sout () {
      this.kind = ''
    }
  }
}
</script>

<style lang="scss">

</style>
