<template>
  <div v-if="!$q.screen.lt.sm" class="q-py-md q-pl-md">
  <div class="q-gutter-y-md q-flex" style="height: 100%; min-height: 400px;" >
  <div class="q-pa-md q-ma-lg">
    <div class="q-gutter-y-md q-flex full-width" style="height: 100%; min-height: 500px; max-height: 600px;">
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
        <div style="height: 100%; min-width: 300px;"
              :class="{'hidden': activeCardIndex !== index }">
            <q-card class="full-height q-pl-md">
              <q-card-section class="text-h5 text-bold">
                {{ text.titulo }}
              </q-card-section>
              <q-card-section horizontal class="row" style="height: calc(100% - 135px)">
                <q-card-section class="col">
                  Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque sagittis ante in vestibulum volutpat. In convallis dui est, quis tincidunt felis ultrices ac. Nunc luctus, odio et luctus facilisis, nisi dui fermentum libero, et placerat justo lacus sed nisl. Curabitur eu sem ut leo dictum consectetur pharetra imperdiet neque.
                  <q-card-section class="flex justify-end" style="padding-left: 0;">
                    <q-btn class="" v-bind:label="text.btn.texto" v-bind:color="text.btn.color" no-caps></q-btn>
                  </q-card-section>
                </q-card-section>
                  <q-img
                    class="col"
                    ratio="1"
                    style="object-fit: cover;"
                    src="https://cdn.quasar.dev/img/parallax2.jpg"
                  />
              </q-card-section>
            </q-card>
          </div>
      </div>
    </div>
    </div>
  </div>
  </div>
  <!--Version  vertical-->
  <div v-else class="q-pa-md">
    <q-list v-for="(item, index) in texts" :key="index" bordered class="q-flex rounded-borders" >
      <q-expansion-item
          group="list"
          v-model="selected_model[item.titulo]"
          expand-separator
          default-opened
          :icon="item.icono"
          :label="item.titulo"
          :header-class="[item.headerClass, 'bg-'+ item.color]"
          style="width: 100%"
          dense-toggle
          expand-icon-class="text-white"
          class="item_section"
        >
        <q-card class="full-height">
            <q-card-section class="text-h5">
              {{ item.titulo }}
            </q-card-section>
            <q-card-section>
              <q-img
                  class="col-5"
                  src="https://cdn.quasar.dev/img/parallax2.jpg"
                />
              <q-card-section class="q-px-none ">
                <p class="item-text-section">{{ item.content }}</p>
              </q-card-section>
            </q-card-section>
            <q-card-section >
              <q-btn :label="item.btn.texto" :color="item.btn.color"  no-caps></q-btn>
            </q-card-section>
          </q-card>
      </q-expansion-item>
    </q-list>
  </div>

</template>

<script setup>
import { ref } from 'vue';

const  selected_model = ref({})

let isExpanded = ref(false)
const texts = [
                {
                  titulo:"Texto 1",
                  color:'orange',
                  headerClass: 'text-white',
                  icono:'warning',
                  btn: {
                        color: 'red',
                        texto:'Ver más'
                      },
                  content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque sagittis ante in vestibulum volutpat. In convallis dui est, quis tincidunt felis ultrices ac. Nunc luctus, odio et luctus facilisis, nisi dui fermentum libero, et placerat justo lacus sed nisl. Curabitur eu sem ut leo dictum consectetur pharetra imperdiet neque.\n'
                  },
                {
                  titulo:"Texto 2",
                  color:'orange-8',
                  headerClass: 'text-white',
                  icono:'warning',
                  btn: {
                        color: 'blue',
                        texto:'Ver menos'
                      },
                  content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque sagittis ante in vestibulum volutpat. In convallis dui est, quis tincidunt felis ultrices ac. Nunc luctus, odio et luctus facilisis, nisi dui fermentum libero, et placerat justo lacus sed nisl. Curabitur eu sem ut leo dictum consectetur pharetra imperdiet neque.\n'
                  },
                {
                  titulo:"Texto 3",
                  color:'orange-4',
                  headerClass: 'text-white',
                  icono:'warning',
                  btn: {
                        color: 'green',
                        texto:'Ver'
                        },
                  content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Pellentesque sagittis ante in vestibulum volutpat. In convallis dui est, quis tincidunt felis ultrices ac. Nunc luctus, odio et luctus facilisis, nisi dui fermentum libero, et placerat justo lacus sed nisl. Curabitur eu sem ut leo dictum consectetur pharetra imperdiet neque.\n'
                  }
            ];

const isActive = ref(false)
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
<style>
.q-flex {
  display: flex;
}

.item_section{
  font-size: 20px !important;
}

.item-text-section{
  font-size: 14px !important;
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
