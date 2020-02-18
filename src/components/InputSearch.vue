<template >
  <div id="noteArea">
    <div id="noteInput" @click="handleClick" >
      <div contenteditable="true" @keyup.enter.self.prevent="handlePress" id="titleTextArea"></div>
      <div contenteditable="true" @keyup.enter="handlePress" id="contentTextArea"></div>
    </div>
    <div id="createNote">
      <!--            <span class="countWord" v-if="wordCount"> {{ wordCount <= 1 ? 'word' : 'words' }}: {{ wordCount }}</span>-->
    </div>
  </div>
</template>
<script>
export default {
    name: 'InputSearch',
    props: {
        msg: String
    },
    data() {
        return {
            noteInput: {
                title: '',
                content: '',
            },
        }
    },
    methods: {
        handlePress(e) {
// console.log(e)
// if (e.key === 'Enter')
// {
//     console.log('test')
//     e.stopImmediatePropagation();
// }
            if (e.target === document.querySelector("#titleTextArea"))
                document.querySelector("#contentTextArea").focus()
        },
        handleClick(e) {
            if (document.querySelector("#contentTextArea").contains(e.target))
                return

            document.querySelector ("#titleTextArea").focus()
        },
        createNote() {
            const titleContent = document.querySelector('#titleTextArea').innerText
            const textContent = document.querySelector('#contentTextArea').innerText

            if (!titleContent && !textContent)
                return

            this.$emit('new-note', {
                id: Date.now() + Math.random(),
                text: textContent,
                title: titleContent,
                wordCount: this.wordCount,
                isEditing: false,
                textEditing: '',
            })

            this.noteInput = ''
        },
    },
    computed: {
        wordCount: function () {
            const textContent = document.querySelector('#contentTextArea').innerText

            if (textContent)
                return

            console.log(textContent.trim().split(' ').length)

            return textContent.trim().split(' ').length
        }
    }
}
</script>

<style>
  #noteArea {
    height: 100vh;
    width: 50vw;
    position: relative;
  }
  #noteInput {
    outline: none;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    border-left: 1px solid #c7c5b7;
    align-items: center;
    color: #37352f;
    background-color: #ffffff;
    box-sizing: border-box;
  }
  #titleTextArea {
    min-height: 46px;
    font-size: 2.4em;
    width: 80%;
    margin-top: 80px;
    word-break: break-word;
    outline: unset;
  }
  #contentTextArea {
    outline: unset;
    padding: 50px;
    margin-top: 100px;
    width: 80%;
    min-height: 20px;
  }
  #createNote{
    position: absolute;
    bottom: 20px;
    right: 10px;
  }
</style>

