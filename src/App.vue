<template>
  <div id="app">
    <div id="noteContainer">
      <div class="notes">
        <?xml version="1.0" encoding="iso-8859-1"?>
        <svg version="1.1" id="Layer_1" @click="newNote" xmlns="http://www.w3.org/2000/svg"
             xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
             viewBox="0 0 492 492" style="enable-background:new 0 0 492 492;" xml:space="preserve">
<g>
	<g>
		<path d="M465.064,207.566l0.028,0H284.436V27.25c0-14.84-12.016-27.248-26.856-27.248h-23.116
			c-14.836,0-26.904,12.408-26.904,27.248v180.316H26.908c-14.832,0-26.908,12-26.908,26.844v23.248
			c0,14.832,12.072,26.78,26.908,26.78h180.656v180.968c0,14.832,12.064,26.592,26.904,26.592h23.116
			c14.84,0,26.856-11.764,26.856-26.592V284.438h180.624c14.84,0,26.936-11.952,26.936-26.78V234.41
			C492,219.566,479.904,207.566,465.064,207.566z"/>
	</g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
</svg>
      </div>
      <div class="notes" v-if="notes" v-for="note in notes">
        <span>{{ note.title }}</span>
        <!--          <span class="countWord" > {{ note.wordCount <= 1 ? 'word' : 'words' }}: {{ note.wordCount }}</span>-->
        <svg version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"
             x="0px" y="0px"
             viewBox="0 0 475.2 475.2" style="enable-background:new 0 0 475.2 475.2;" xml:space="preserve">
<g>
	<g>
		<path d="M405.6,69.6C360.7,24.7,301.1,0,237.6,0s-123.1,24.7-168,69.6S0,174.1,0,237.6s24.7,123.1,69.6,168s104.5,69.6,168,69.6
			s123.1-24.7,168-69.6s69.6-104.5,69.6-168S450.5,114.5,405.6,69.6z M386.5,386.5c-39.8,39.8-92.7,61.7-148.9,61.7
			s-109.1-21.9-148.9-61.7c-82.1-82.1-82.1-215.7,0-297.8C128.5,48.9,181.4,27,237.6,27s109.1,21.9,148.9,61.7
			C468.6,170.8,468.6,304.4,386.5,386.5z"/>
    <path d="M342.3,132.9c-5.3-5.3-13.8-5.3-19.1,0l-85.6,85.6L152,132.9c-5.3-5.3-13.8-5.3-19.1,0c-5.3,5.3-5.3,13.8,0,19.1
			l85.6,85.6l-85.6,85.6c-5.3,5.3-5.3,13.8,0,19.1c2.6,2.6,6.1,4,9.5,4s6.9-1.3,9.5-4l85.6-85.6l85.6,85.6c2.6,2.6,6.1,4,9.5,4
			c3.5,0,6.9-1.3,9.5-4c5.3-5.3,5.3-13.8,0-19.1l-85.4-85.6l85.6-85.6C347.6,146.7,347.6,138.2,342.3,132.9z"/>
	</g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
          <g>
</g>
</svg>
      </div>
    </div>
    <!--  <inputsearch @new-note="submitNote"></inputsearch>-->
    <InputSearch/>
    <div id="note">
      {{note}}
    </div>
  </div>

</template>

<script>
    import InputSearch from './components/InputSearch.vue'

    export default {
        name: 'App',
        components: {
            InputSearch,
        },
        data() {
            return {
                note: '',
                notes: [],
            }
        },
        methods: {
            deleteNote(note) {
                this.notes = this.notes.filter(el => el.id !== note.id)

                localStorage.setItem('notes', JSON.stringify(this.notes))
            },
            revealNote(note) {
                this.$emit('reveal-note', note)
            },
            newNote() {
                this.$emit('new_note')

                this.notes.push({
                    id: Date.now() + Math.random(),
                    text: '',
                    title: 'untitled',
                    wordCount: undefined,
                })
            },

            // willEditIt(note) {
            //     this.notes = this.notes.map(el => {
            //         if (el.id !== note.id)
            //             return el
            //
            //         return {
            //             ...el,
            //             isEditing: true,
            //             textEditing: el.text,
            //         }
            //     })
            //     localStorage.setItem('notes', JSON.stringify(this.notes))
            // },
            // editNote(note) {
            //     this.notes = this.notes.map(el => {
            //         if (el.id !== note.id)
            //             return el
            //
            //         const text = note.textEditing.trim() ? note.textEditing : el.text
            //
            //         return {
            //             ...el,
            //             text,
            //             isEditing: false,
            //             wordCount: this.wordCount(text)
            //         }
            //     })
            //     localStorage.setItem('notes', JSON.stringify(this.notes))
            // },
            wordCount(text) {
                if (!text)
                    return

                return text.trim().split(' ').length
            },
        },
        mounted: function () {
            if (localStorage.notes)
                return

            this.notes = JSON.parse(localStorage.notes)

            document.querySelector('#titleTextArea').addEventListener('keyup', (e) => {
                if (e.key === 'Enter') {
                    console.log(e)

                    e.stopImmediatePropagation();
                }
            }, false)
        }
    }


</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
