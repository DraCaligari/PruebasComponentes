<template>
  <div class="q-py-md q-pl-md q-ma-lg">
    <div class="q-gutter-y-md q-flex" style="height: 100%; min-height: 500px;">
      <div v-for="(text, index) in texts" :key="index" class="q-flex">
        <div class="content1" style="width: 62px!important; height: 100%;">
          <q-card
            v-bind:class="text.color === null ? 'text-primary' : 'bg-' + text.color"
            class="text-white"
            ref="cards"
            style="height: 100%;"
            @click="toggleCard(index)"
          >
              <q-card-section class="q-pa-md">
                <q-icon name="warning" size="1.5em" class="q-mb-md row q-flex justify-center full-width"></q-icon>
                <p :class="{'text-weight-bold': activeCardIndex === index }" class="vertical-text text-center text-h6 row q-flex justify-center items-center full-width">{{ text.titulo }}</p>
              </q-card-section>
            </q-card>
        </div>
          <div style="height: 100%; min-width: 300px; max-width: 800px;"
              :class="{'hidden': activeCardIndex !== index }">
            <q-card class="full-height q-pl-md">
              <q-card-section class="text-h5 text-bold">
                {{ text.titulo }}
              </q-card-section>
              <q-card-section horizontal class="row">
                <q-card-section class="col">
                  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque sagittis ante in vestibulum volutpat. In convallis dui est, quis tincidunt felis ultrices ac. Nunc luctus, odio et luctus facilisis, nisi dui fermentum libero, et placerat justo lacus sed nisl. Curabitur eu sem ut leo dictum consectetur pharetra imperdiet neque.
                </q-card-section>
                  <q-img
                    class="col"
                    :ratio=1
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

let isExpanded = ref(false)
const texts = ref([{titulo:"Texto 1", color:'orange', icono:'mdi-cow'},{titulo:"Texto 2", color:'orange-8',icono:'mdi-cow'}, {titulo:"Texto 3", color:'orange-4', icono:'mdi-cow'}]);
const activeCardIndex = ref(0);

const toggleCard = (index) => {
  if (activeCardIndex.value === index) {
    isExpanded.value = !isExpanded.value;
  } else {
  isExpanded.value = !isExpanded.value;
  activeCardIndex.value = index;
  }
};

</script>
<style scoped>
.q-flex {
  display: flex;
}

.horizontal-card {
  flex: 1;
  text-align: center;
  max-width: 200px; /* Ajusta según tus necesidades */
  position: relative;
}
.q-card{
  border-radius: 0!important;
}
.vertical-text {
  writing-mode: vertical-rl;
  transform: rotate(180deg);
  white-space: nowrap;
}
</style>
