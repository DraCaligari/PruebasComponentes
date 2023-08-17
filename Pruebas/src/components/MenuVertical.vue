<template>
  <div class="q-py-md q-pl-md">
    <div class="q-gutter-y-md q-flex" style="height: 100%; min-height: 400px;">
      <div v-for="(text, index) in texts" :key="index" class="q-flex">
        <div class="content1" style="width: 50px!important; height: 100%;">
          <q-card
            class="horizontal-card"
            ref="cards"
            style="width: 50px!important; height: 100%;"
            @click="toggleCard(index)"
          >
              <q-card-section class="q-pa-md">
                <p class="vertical-text">{{ text }}</p>
              </q-card-section>
            </q-card>
        </div>
        <div style="height: 100%; min-width: 500px; max-width: 500px;" :class="{ 'hidden': activeCardIndex !== index }">
          <q-card class="full-height">
            <q-card-section class="text-h5">
              {{ text }}
            </q-card-section>
            <q-card-section horizontal>
              <q-card-section>
                Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque sagittis ante in vestibulum volutpat. In convallis dui est, quis tincidunt felis ultrices ac. Nunc luctus, odio et luctus facilisis, nisi dui fermentum libero, et placerat justo lacus sed nisl. Curabitur eu sem ut leo dictum consectetur pharetra imperdiet neque.
              </q-card-section>
                <q-img
                  class="col-5"
                  src="https://cdn.quasar.dev/img/parallax2.jpg"
                />
            </q-card-section>
            <q-card-section>
              <q-btn label="Ver más"></q-btn>
            </q-card-section>
          </q-card>
        </div>
      </div>
    </div>
  </div>


</template>

<script setup>
import { ref } from 'vue';

const texts = ref(["Texto 1", "Texto 2", "Texto 3"]);
const activeCardIndex = ref(0);

const toggleCard = (index) => {
    console.log(activeCardIndex.value)
  if (activeCardIndex.value === index) {
    //activeCardIndex.value = -1;
      //console.log(activeCardIndex.value, 'if')
  } else {
    activeCardIndex.value = index;
      console.log(activeCardIndex.value, 'else')
  }
};

//toggleCard(null);

</script>

<style scoped>
/*.content1:hover+.content2 {*/
/*  display: flex !important;*/
/*}*/

/*.content1-container:hover .content2 {*/
/*  display: block;*/
/*}*/

.q-flex {
  display: flex;
}

.horizontal-card {
  flex: 1;
  text-align: center;
  max-width: 200px; /* Ajusta según tus necesidades */
  position: relative;
}

.vertical-text {
  writing-mode: vertical-rl;
  transform: rotate(180deg);
  white-space: nowrap;
}
</style>
