<template lang="pug">

  .DIV
    p Выбрать город РФ
    pre {{selected}}
    input.Serch(
      v-model="keyword",
      @keyup.delete="selected.city?selected={}:''",
      @keydown.down='moveDown', 
      @keydown.up='moveUp',
      @keydown.enter='onSelect(filteredItems[highlight])',
      @input="onInput($event.target.value)")
    p(v-show="!test", style="color:red") Кирилицей !
    ul.filteredItems(
      v-show="keyword && !selected.city")
      li(
        v-for="(item,i) in filteredItems", 
        :key="item.city",
        :class="{highlight:i==highlight}",
        @mouseenter='highlight = i',
        @click="onSelect(item)",
        v-html="mark(item.city)")

    p Выбирите город. Набирать кирилицей
</template>

<script>
export default {
  //name: 'autocomplete',
  props: {
    str: {
      type: String,
      default: ""
    }
  },
  data() {
    return {
      keyword: "",
      test: true,
      dataList: [],
      selected: {},
      highlight: 0
    };
  },
  computed: {
    filteredItems() {
      return this.dataList
        .filter(item => {
          return item.city.toLowerCase().includes(this.keyword.toLowerCase());
        })
        .slice(0, 10);
    }
  },
  methods: {
    onInput(value) {
      if (this.filteredItems.length == 1 && this.highlight) this.highlight = 0;
      this.test = /^[ а-яА-я]/.test(this.keyword);
    },
    onSelect(val) {
      this.selected = val;
      this.keyword = this.selected.city;
      //
      this.highlight = 0;
    },
    moveDown() {
      //this.highlight++
      if (!this.keyword) return;
      this.highlight = (this.highlight + 1) % this.filteredItems.length;
    },
    moveUp() {
      if (!this.keyword) return;
      this.highlight =
        this.highlight - 1 < 0
          ? this.filteredItems.length - 1
          : this.highlight - 1;
    },
    mark(word) {
      const regex = new RegExp("(" + this.keyword + ")", "gi");
      return word.replace(regex, "<mark>$1</mark>");
    }
  },
  mounted() {
    fetch(
      "https://gist.githubusercontent.com/gorborukov/0722a93c35dfba96337b/raw/435b297ac6d90d13a68935e1ec7a69a225969e58/russia"
    )
      .then(r => r.json())
      .then(data => (this.dataList = data));
  }
};
</script>





<style lang="stylus">
@import '../assets/settings';

.DIV {
  margin: 1em;
  display: inline-block;
  position: relative;
}

// UL
.filteredItems {
  position: absolute;
  margin-top: -1em; // !FIXME
  width: 100%;
  background: #FFF;
  box-shadow: 0 0.2em 1.4em 0 rgba(0, 0, 0, 0.2);

  li {
    padding: 0.5em;
    padding-left: 1em;
    cursor: pointer;
    list-style: none;
    color: #477dca;
    border-top: 1px solid #EFEFEF;

    &.highlight {
      color: #000;
      background: #f9f9f9;
    }
  }
}
</style>
