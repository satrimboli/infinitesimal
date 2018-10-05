<template>
  <div id="app">
    <div class='type-canvas'>
      <div v-for="(verse, verseIndex) in lyrics" :class="['verse-' + ( verseIndex + 1)]">
        <div v-for="(line, lineIndex) in verse" :class="['line-' + ( lineIndex + 1), line.classes]" v-if="line.phrases">
          <TypeUnit v-for="(phrase, phraseIndex) in line.phrases" :class="['phrase-' + ( phraseIndex + 1)]" :start="phrase.start || line.start" :end="phrase.end || line.end" :currentTime="currentTime" :cssClasses="phrase.classes">
            {{phrase.text}}
          </TypeUnit>
        </div>
        <TypeUnit v-else :class="['line-' + ( lineIndex + 1), line.classes]" :start="line.start" :end="line.end" :currentTime="currentTime">
          {{line.text}}
        </TypeUnit>
      </div>      
    </div>

    <audio ref='audio' src="infinitesimal.mp3" controls @canplaythrough.once="setCurrentTime" @timeupdate="updateCurrentTime" />
  </div>
</template>

<script>
import TypeUnit from './components/type-unit.vue'

export default {
  name: 'app',
  components: {
    TypeUnit
  },
  data: function() {
    return {
      currentTime: 14,
      lyrics: [
        // verse
        [
          // line
          {
            start: 18,
            end: 22,
            phrases: [
              // phrase
              { text: 'There\'s a' },
              { text: 'million', classes: 'text--large' },
              { text: 'billion', classes: 'text--large' },
              { text: 'trillion', classes: 'text--large' },
              { text: 'stars' }
            ]
          }, {
            start: 22,
            end: 25,
            phrases: [
              { text: 'but i\'m down here low', classes: 'text--center-bottom' },
              { text: 'fussin over scars', start: 24 , classes: '' },
            ],
          }, {
            end: 30,
            phrases: [
              { text: 'on my soul', start: 25.5 },
              { text: 'on my soul', start: 26.5 },
              { text: 'on my soul', start: 27.5 },
              { text: 'on my soul', start: 28.5 },
              { text: 'on my soul', start: 29.5 }
            ],
          }, {
            end: 34,
            phrases: [
              { text: 'I am so', start: 30 },
              { text: 'infinitesimal', start: 31.5 },
              { text: 'oh', start: 33 }
            ]
          }
        ], [
          {
            start: 36,
            end: 38,
            phrases: [
              { text: 'they say', start: 34 },
              { text: 'it started with a', start: 35.5 },
              { text: 'big' },
              { text: 'bang' }
            ],
          }, {
            end: 40,
            phrases: [
              { text: 'but they say', start: 38 },
              { text: 'it came out of a', start: 39},
              { text: 'small thing', start: 40 }
            ]
          }, {
            end: 50,
            phrases: [
              { text: 'Lately', start: 42 },
              { text: 'I\'m feeling like a big bang', start: 43 }
            ]
          }, {
            end: 50,
            phrases: [
              { text: 'Cause I\'ve been making', start: 45 },
              { text: 'something out of nothing', start: 47 }
            ]
          }
        ], [
          {
            phrases: [
              { text: 'millions and billions and trillions of stars', start: 56},
              { text: 'but i\'m down here low', start: 60 },{
                text: 'fussing over scars'
              }, 
            ]
          }, {
            phrases: [
              { text: 'on my soul' },
              { text: 'on my soul' },
              { text: 'on my soul' },
              { text: 'on my soul' },
              { text: 'on my soul' }
            ],
          }, {
            phrases: [
              { text: 'I am so' },
              { text: 'infinitesimal' },
              { text: 'oh' }
            ]
          }
        ], [
          {
            phrases: [
              { text: 'they say' },
              { text: 'it started with a' },
              { text: 'big' },
              { text: 'bang' }
            ],
          }, {
            phrases: [
              { text: 'but they say' },
              { text: 'it was really just a ' },
              { text: 'small thing' }
            ]
          }, {
            phrases: [
              { text: 'Lately' },
              { text: 'I\'m feeling like a big bang' }
            ]
          }, {
            phrases: [
              { text: 'Cause I\'ve been making' },
              { text: 'something out of nothing' }
            ]
          }
        ], [
          {
            text: 'Do you ever really think about the grains?'
          }, {
            text: 'Every little one\'s got a million things'
          }, {
            phrases: [
              { text: "Every little bit’s got a billion bits, and that ain’t it, no that ain’t it" }
            ]
          }, {
            phrases: [
              { text: "And did you know that when you really get close" }
            ]
          }, {
            phrases: [
              { text: "Nothing really touches, bro, just kind of floats?" }
            ]
          }, {
            phrases: [
              { text: "So when you think it might just come to blows" }
            ]
          }, {
            phrases: [
              { text: "Just so you know, it won’t, cause it can’t, bro" }
            ]
          }
        ], [
          // line
          {
            phrases: [
              // phrase
              { text: 'There\'s a' },
              { text: 'million', classes: 'text--large' },
              { text: 'billion', classes: 'text--large' },
              { text: 'trillion', classes: 'text--large' },
              { text: 'stars' }
            ]
          }, {
            phrases: [
              { text: 'but i\'m down here low', classes: 'text--center-bottom' },
              { text: 'fussin over scars', classes: '' },
            ],
          }, {
            phrases: [
              { text: 'on my soul' },
              { text: 'on my soul' },
              { text: 'on my soul' },
              { text: 'on my soul' },
              { text: 'on my soul' }
            ],
          }, {
            phrases: [
              { text: 'I am so' },
              { text: 'infinitesimal' },
              { text: 'oh' }
            ]
          }
        ], [
          {
            phrases: [
              { text: 'they say' },
              { text: 'it started with a' },
              { text: 'big' },
              { text: 'bang' }
            ],
          }, {
            phrases: [
              { text: 'but they say' },
              { text: 'it was really just a ' },
              { text: 'small thing' }
            ]
          }, {
            phrases: [
              { text: 'Lately' },
              { text: 'I\'m feeling like a big bang' }
            ]
          }, {
            phrases: [
              { text: 'Cause I\'ve been making' },
              { text: 'something out of nothing' }
            ]
          }
        ], [
          {
            text: "Like my soul, just like my soul, you think it’s so infinitesimal" 
          }
        ]
      ]
    }
  },
  methods: {
    setCurrentTime: function() {
      this.$refs.audio.currentTime = 18;
    },

    updateCurrentTime: function() {
      this.currentTime = this.$refs.audio.currentTime
    }
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}

html, body {
  height: 100%;
}

body {
  margin: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
  display: flex;
  flex-direction: column;
}

.type-canvas {
  padding: 50px;
  flex: 1;
  width: 100%;
  border: 1px solid #000;

  background: #222;
  color: #ddd;

  text-align: center;
  font-size: 16px;
}

.is-hidden {
  opacity: 0;
}

.is-visible {
  opacity: 1;
  transition: opacity 1s;
}

.vertically-centered {
  position: relative;
  top: 50%;
  transform: translateY(-50%);
}

.slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-leave-active {
  transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}

audio {
  margin: 0 auto;
}

.type-canvas {
  text-transform: uppercase;
}

/* .text--large {
  font-size: 10em;
  line-height: 1;
} */
</style>
