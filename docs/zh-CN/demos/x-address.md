---
nav: zh-CN
---


### XAddress_COM

<img width="100" src="http://qr.topscan.com/api.php?text=https%3A%2F%2Fvux.li%2Fdemos%2Fv2%2F%23%2Fcomponent%2Fx-address"/>

<a href="https://vux.li/demos/v2/#/component/x-address" target="_blank" style="font-size:12px;color:#888;">demo 原始链接：https://vux.li/demos/v2/#/component/x-address</a>



---

#### 演示

 <div style="width:377px;height:667px;display:inline-block;border:1px dashed #ececec;border-radius:5px;overflow:hidden;">
   <iframe src="https://vux.li/demos/v2/#/component/x-address" width="375" height="667" border="0" frameborder="0"></iframe>
 </div>

#### demo 代码

<p class="tip">下面的$t是Demo的i18n使用的翻译函数，一般情况下可以直接使用字符串。另外，下面代码隐藏了i18n标签部分的代码。</p>

``` html
<template>
  <div>
    <group>
      <x-address @on-hide="logHide" @on-show="logShow" :title="title" v-model="value" :list="addressData" placeholder="请选择地址" inline-desc="可以设置placeholder"></x-address>
      <cell title="上面value值" :value="value"></cell>
    </group>
    <br>
    <group label-width="4em" label-align="left">
      <x-address :title="title2" v-model="value2" raw-value :list="addressData" value-text-align="left"></x-address>
    </group>
    <br/>
    <div style="padding: 0 15px;">
      <x-button type="primary" @click.native="changeData">改变数据</x-button>
    </div>
    <br/>

    <group>
      <x-address title="二级省市" v-model="value3" raw-value :list="addressData"></x-address>
    </group>
    <group>
      <x-address title="只显示省市" v-model="value4" raw-value :list="addressData" hide-district></x-address>
      <cell title="value值" :value="value4"></cell>
      <cell title="转换成文字值" :value="getName(value4)"></cell>
    </group>

    <br/>
    <group title="错误的地址将不能正确渲染到相应位置">
      <x-address title="错误的值" v-model="value5" raw-value :list="addressData" inline-desc="广东省, 深圳 市, 南山区"></x-address>
    </group>
  </div>
</template>

<script>
import { Group, XAddress, ChinaAddressV3Data, XButton, Cell, Value2nameFilter as value2name } from 'vux'

export default {
  components: {
    Group,
    XAddress,
    XButton,
    Cell
  },
  data () {
    return {
      title: '默认为空',
      value: [],
      title2: '设置值',
      value2: ['天津市', '市辖区', '和平区'],
      value3: ['广东省', '中山市', '--'],
      addressData: ChinaAddressV3Data,
      value4: [],
      value5: ['广东省', '深圳 市', '南山区']
    }
  },
  methods: {
    changeData () {
      this.value2 = ['430000', '430400', '430407']
    },
    getName (value) {
      return value2name(value, ChinaAddressV3Data)
    },
    logHide (str) {
      console.log('on-hide', str)
    },
    logShow (str) {
      console.log('on-show')
    }
  }
}
</script>

```


#### Github Issue