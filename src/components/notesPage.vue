<template>
  <section class="section">
    <div class="section-content">
      <div class="allow-edit-container">
        <button class="allow-edit" @click="allowEdit = !allowEdit">Редактировать</button>
        <h3>Количество записей: {{ countNotes }}</h3>
      </div>
      <article v-for="(note, index) in notes" :key="index" class="note">
        <div >{{ note.name }}</div>
        <div v-if="currentItem !== index">{{ note.value }}</div>
        <input type="text" v-model="activeInput" v-else class="input">
        <div class="btn-container" :class="{'vis': !allowEdit}">
          <button @click="openChange(note.value, index)" v-if="currentItem !== index" class="edit"></button>
          <button @click="saveChange(index)" v-else class="save"></button>
        </div>
      </article>
    </div>
  </section>
</template>
<script setup>
import { ref } from 'vue';
const notes = ref([
  {
    name: 'foo1',
    value: 'bar1'
  },
  {
    name: 'foo2',
    value: 'bar2'
  },
  {
    name: 'foo3',
    value: 'bar3'
  },
  {
    name: 'foo4',
    value: 'bar4'
  },
  {
    name: 'foo5',
    value: 'bar5'
  },
  {
    name: 'foo6',
    value: 'bar6'
  },
  {
    name: 'foo7',
    value: 'bar7'
  },
  {
    name: 'foo8',
    value: 'bar8'
  },
  {
    name: 'foo9',
    value: 'bar9'
  },
  {
    name: 'foo10',
    value: 'bar10'
  },
  {
    name: 'foo11',
    value: 'bar11'
  },
  {
    name: 'foo12',
    value: 'bar12'
  },
  {
    name: 'foo13',
    value: 'bar13'
  },
  {
    name: 'foo14',
    value: 'bar14'
  },
  {
    name: 'foo15',
    value: 'bar15'
  },
  {
    name: 'foo16',
    value: 'bar16'
  },
  {
    name: 'foo17',
    value: 'bar17'
  },
  {
    name: 'foo18',
    value: 'bar18'
  },
  {
    name: 'foo19',
    value: 'bar19'
  },
  {
    name: 'foo20',
    value: 'bar20'
  },
  {
    name: 'foo21',
    value: 'bar21'
  },
  {
    name: 'foo21',
    value: 'bar21'
  },
  {
    name: 'foo22',
    value: 'bar22'
  },
  {
    name: 'foo23',
    value: 'bar23'
  },
  {
    name: 'foo24',
    value: 'bar24'
  },
  {
    name: 'foo25',
    value: 'bar25'
  },
  {
    name: 'foo26',
    value: 'bar26'
  },
  {
    name: 'foo27',
    value: 'bar27'
  },
  {
    name: 'foo28',
    value: 'bar28'
  },
  {
    name: 'foo29',
    value: 'bar29'
  }
])
const activeInput = ref('')
const currentItem = ref(null)
const allowEdit = ref(false)
const countNotes = ref(notes.value.length - 1)
const openChange = (value, i) => {
  currentItem.value = i
  activeInput.value = value
}
const saveChange = (index) => {
  notes.value[index].value = activeInput.value
  currentItem.value = null
}
</script>
<style scoped>
.note{
  width: 200px;
  height: 100px;
  padding: 10px;
  background: #F5F6F7;
  border-radius: 20px;
  box-shadow: 0px 0px 3px rgba(3, 3, 3, 0.212);
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  transition: all 0.4s linear;
  position: relative;
}
.note:hover{
  transition: all 0.4s linear;
  background: #abaaaa66;
}
.section{
  width: 100vw;
  height: 100vh;
  background-image: url('../assets/Vector.svg');
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgba(28, 26, 26, 0.97);
}
.section-content{
  max-width: 59vw;
  height: 60vh;
  overflow-y: scroll;
  margin: 0 auto;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 15px;
  padding: 0 30px 30px;
  background: #F5F6F7;
  border-radius: 20px;
  box-shadow: 3px 3px 3px rgba(128, 128, 128, 0.212);
}
.input {
  width: 100%;
  border: 1px solid #F0EFF2;
  border-radius: 10px;
  padding: 5px 10px;
}
.edit{
  border: 1px solid rgba(0, 0, 0, 0.721);
  border-radius: 100px;
  background-color: none;
  width: 30px;
  height: 30px;
  cursor: pointer;
  background-image: url('../assets/edit.svg');
}
.save{
  border-radius: 100px;
  border: none;
  cursor: pointer;
  background-color: none;
  width: 30px;
  height: 30px;
  background-image: url('../assets/save.svg');
}
.btn-container{
  position: absolute;
  top: 10px;
  right: 10px;
}
.allow-edit-container{
  width: 100%;
  height: 53px;
  position: sticky;
  top: 0;
  background-color: #F5F6F7;
  z-index: 2;
  padding-top: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
}
.allow-edit{
  height: 44px;
  background: #cccccc;;
  border: none;
  border-radius: 10px;
  font: 700 16px / 20px 'Helvetica';
  padding: 10px;
  cursor: pointer;
}
.vis{
  visibility: hidden;
}
@media(max-width:800px){
  .allow-edit-container{
    height: 93px;
    flex-direction: column;
    align-items: center;
  }
}
@media(max-width:500px){
  .section-content{
    max-width: 90%;
    justify-content: center;
  }
}
</style>