<template>
  <div id="app">
    <h2>配色表</h2>
    <ul>
      <li class="vd-default">#FFFFFF</li>
      <li class="vd-success">#9EDE73</li>
      <li class="vd-warning">#E48900</li>
      <li class="vd-danger">#BE0000</li>
      <li class="vd-info">#536162</li>
      <li class="vd-primary">#214252</li>
    </ul>
    <h2>vd-button</h2>
    <vd-button @click="click1"> default </vd-button>
    <vd-button @click="click1" :disabled="true"> disabled </vd-button>
    <h3>type</h3>
    <vd-button type="primary"> primary </vd-button>
    <vd-button type="success"> success </vd-button>
    <vd-button type="info"> info </vd-button>
    <vd-button type="warning"> warning </vd-button>
    <vd-button type="danger"> danger </vd-button>
    <h3>size</h3>
    <vd-button size="mini"> mini </vd-button>
    <vd-button size="medium"> medium </vd-button>
    <vd-button size="large"> large </vd-button>
    <h2>vd-card</h2>
    <vd-card style="width: 400px; max-width: 88vw">
      <div slot="header" class="flex">
        <span class="f1">安墨对我说</span>
        <span class="f-s12"> ✅ 收藏</span>
      </div>
      <p class="t-i2">
        当你低着头只是一个劲地努力着，行走着，进行着，忽然抬头，发现自己已经站在曾经想要站着的位置了
      </p>
      <p class="t-r f-s12">——丶安墨</p>
      <p class="t-r f-s12">2021/2/1 22:39</p>
    </vd-card>
    <br />
    <vd-card style="width: 400px; max-width: 88vw" type="primary">
      <div slot="header">安墨对我说</div>
      <p class="t-i2">
        当你低着头只是一个劲地努力着，行走着，进行着，忽然抬头，发现自己已经站在曾经想要站着的位置了
      </p>
      <p class="t-r f-s12">——丶安墨</p>
      <p class="t-r f-s12">2021/2/1 22:39</p>
    </vd-card>
    <h2>vd-input</h2>
    <h3>基础使用</h3>
    <vd-input />
    <h3>type</h3>
    <vd-input placeholder="输入用户名" type="text" />
    <br />
    <vd-input placeholder="输入密码" type="password" />
    <h3>限制长度</h3>
    <vd-input type="text" maxlength="10" />
    <br />
    <vd-input type="text" maxlength="10" after="length" />
    <h3>双向绑定</h3>
    <vd-input type="text" :vModel.sync="value" />
    <p>value = {{ value }}</p>
    <vd-progress :color="colorsData" :percent="data1" width="300px" />
    <br>

    <vd-progress color="red" :percent="data1" width="300px" />
    <br>
    <vd-progress :percent="10" width="300px" />
    <br>

    <vd-progress :color="customColorMethod" :percent="data1" width="300px" />
    <br>
    <vd-button @click="data1 += 10"> + </vd-button>
    <vd-button @click="data1 -= 10"> - </vd-button>
    <br>
    <vd-progress :exhibition=" percent => percent >= 100 ? '满' : `${percent}%`" :percent="data1" width="300px" />
    <vd-link type="primary" :underline="false" target="_blank" href="https://baidu.com">链接1</vd-link>
    <br>
     <vd-button type="success" @click="showViewer = true"> 图片查看器 </vd-button>
    <xes-image-viewer v-model="showViewer" :current-image-index="imageIndex" :show-pre-next-bar="true" :close-on-press-escape="false" :img-list="imgList"/>
    <go-top></go-top>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      hhhhhh: 1,
      data1: 10,
      val1: "333",
      value1: "test",
      value: "",
      colorsData: [
        { color: "#be0000", percent: 20 },
        { color: "#e48900", percent: 40 },
        { color: "#9ede73", percent: 60 },
        { color: "#bule", percent: 90 },
      ],
      showViewer: false,
      imageIndex: 0,
      imgList: [
        {
          title: '图片名称1', //可以没有
          url: 'data:image/jpeg;base64,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'
        }, {
          title: '图片名称2', //可以没有
          url: `https://picsum.photos/id/100/1440/900`
        }
      ]
    };
  },
  methods: {
    changeVal() {
      this.data1 += 10;
    },
    customColorMethod(percentage) {
      if (percentage < 30) {
        return 'blue';
      } else if (percentage < 70) {
        return '#e6a23c';
      } else {
        return '#67c23a';
      }
    },
    click1(e) {
      console.log(this.val1);
    },
    change1(v) {
      console.log(1);
    },
    blur1(v) {
      console.log(this.value1);
    },
  },
};
</script>

<style lang="scss">
@import '../common/style/const.scss';
button,
input {
  margin: 6px !important;
}
.flex {
  display: flex;
}
.f1 {
  flex: 1;
  align-items: center;
  justify-content: center;
}
.t-r {
  text-align: right;
}
.f-s12 {
  font-size: 12px;
}
.t-i2 {
  text-indent: 2em;
}
#app {
  padding: 20px;
}
ul {
  border: 1px solid $vd-border;
  display: inline-block;
}
ul > li {
  width: 200px;
  height: 40px;
  text-align: center;
  line-height: 40px;
  color: #fff;
}

.vd-default {
  background-color: $vd-default;
  color: $vd-font;
}
.vd-success {
  background-color: $vd-success;
}
.vd-warning {
  background-color: $vd-warning;
}
.vd-danger {
  background-color: $vd-danger;
}
.vd-info {
  background-color: $vd-info;
}
.vd-primary {
  background-color: $vd-primary;
}
</style>
