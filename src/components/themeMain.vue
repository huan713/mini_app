<template>
  <div class="index-theme">
    <div type="text" class="theme-border">
      <span class="text">
        <span>{{showWords}}</span>
        <span class="cursor" v-if="showCursor"></span>
      </span>
    </div>
    <span class="theme-badge"></span>
  </div>
</template>

<script>
const KEEP_TIME = 5000
const ADD_INTERVAL = 200
const DEL_INTERVAL = 400
export default {
  data () {
    return {
      showCursor: true,
      showWords: '',
      wordsList: [
        '坚持', '远方', '情怀', '小确幸', '希望', '执着', '期待', '痛并快乐', '不再犹豫'
      ],
      cursorLeft: '130rpx',
      adding: false
    }
  },
  mounted () {
    this.blink()
    this.changeWords()
  },
  methods: {
    // 光标闪烁
    blink () {
      if (this.adding) {
        this.showCursor = false
        return
      }

      setTimeout(() => {
        this.showCursor = !this.showCursor
        this.blink()
      }, 600)
    },
    // 改变文字
    changeWords () {
      // 选择文字
      let words = this.chooseWord()
      this._add(words)
    },
    chooseWord () {
      const len = this.wordsList.length
      if (len < 2) return ''

      const index = Math.floor(Math.random() * len)
      let words = this.wordsList[index]
      if (words === this.showWords) {
        this.chooseWord()
      } else {
        return words
      }
    },
    _add (words) {
      if (!words || typeof words !== 'string') return

      let wordArr = words.split('')

      let timer = setInterval(() => {
        this.adding = true
        this.showCursor = false
        let chat = wordArr.shift()
        this.showWords += chat

        if (wordArr.length === 0) {
          this.adding = false
          clearInterval(timer)
          timer = null

          if (!this.showCursor) {
            this.blink()
          }

          setTimeout(() => {
            this._delete()
          }, KEEP_TIME)
        }
      }, ADD_INTERVAL)
    },
    _delete () {
      let timer = setInterval(() => {
        let wordArr = this.showWords.split('')
        wordArr.pop()
        this.showWords = wordArr.join('')

        if (this.showWords === '') {
          clearInterval(timer)
          timer = null

          setTimeout(() => {
            this.changeWords()
          }, 500)
        }
      }, DEL_INTERVAL)
    }
  }
}
</script>

<style lang="less">
.index-theme {
  
  .theme-border {
    width: 72%;
    height: 72rpx;
    margin: 0 auto;
    border: 1px solid rgba(255,255,255,0.6);
    border-radius: 16rpx;
  }
  .theme-badge {
    position: absolute;
    bottom: -16rpx;
    right: 120rpx;
    display: block;
    width: 12rpx;
    height: 8rpx;
    border: 6px solid #000;
    border-bottom-left-radius: 200%;
    border-bottom-right-radius: 200%;
    background-color: rgba(200,200,200,0.5);
  }
  .cursor {
    // position: absolute;
    // top: 18rpx;
    display: inline-block;
    height: 36rpx;
    width: 2rpx;
    background-color: rgba(255,255,255,0.6);
  }
  .text {
    position: absolute;
    top: 12rpx;
    left: 130rpx;
    font-size: 32rpx;
    color: rgba(255,255,255,0.8);

    span {
      vertical-align: bottom;
    }
  }
}
</style>

