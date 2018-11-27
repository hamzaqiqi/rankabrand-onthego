<template>
  <div class="component-score-rects">
      <p>{{ scores[selected].text }}</p>
      <div>
        <div
            v-for="s in Object.keys(scores)"
            :class="{ rect: true, [s]: true, active: score === s, selected: selected === s}"
            @click="selected = s"
        >
            <span>{{ s }}</span>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  name: 'search',
  components: {

  },
  props: {
    score: {
      type: String
    }
  },
  data () {
    return {
      selected: this.score,
      scores: {
        E: {
          text: 'Hand nog even op de knip'
        },
        D: {
          text: 'Eerste mijlpalen bereikt, moet beter'
        },
        C: {
          text: 'Redelijk op weg, kan beter'
        },
        B: {
          text: 'Goed op weg'
        },
        A: {
          text: 'Top mark: kopen!'
        }
      }
    }
  },
  watch: {
    score () {
      this.selected = this.score
    }
  }
}
</script>

<style scoped lang="scss">
@import '../assets/scss/variables.scss';

.component-score-rects {
    width: 100%;
}

p {
    padding: 15px;
}

.rect {
    position: relative;
    width: calc(20% - 18px);
    margin-right: 15px;
    height: 0px;
    padding-top: calc(20% - 18px);
    background-color: #ccc;
    color: #999999;
    display: inline-block;
    font-size: 47px;
    font-weight: bold;
    text-align: center;
    line-height: 64px;
    cursor: pointer;
    position: relative;
    &:first-child {
        margin-left: 15px;
    }
    &.selected:after {
        content: "";
        position: absolute;
        width: 0;
        height: 0;
        border-style: solid;
        border-width: 0 10px 10px 10px;
        border-color: transparent transparent #ccc transparent;
        top: -10px;
        left: calc(50% - 10px);
    }
    
    span {
      width: 100%;
      position: absolute;
      top: calc(50% - 30px);
      left: 0;
    }
}

.A.active {
    background-color: $color-a;
    color: darken($color-a, 20%);
    &.selected:after { border-color: transparent transparent $color-a transparent }
}
.B.active {
    background-color: $color-b;
    color: darken($color-b, 20%);
    &.selected:after { border-color: transparent transparent $color-b transparent }
}
.C.active {
    background-color: $color-c;
    color: darken($color-c, 20%);
    &.selected:after { border-color: transparent transparent $color-c transparent }
}
.D.active {
    background-color: $color-d;
    color: darken($color-d, 20%);
    &.selected:after { border-color: transparent transparent $color-d transparent }
}
.E.active {
    background-color: $color-e;
    color: darken($color-e, 20%);
    &.selected:after { border-color: transparent transparent $color-e transparent }
}
</style>
