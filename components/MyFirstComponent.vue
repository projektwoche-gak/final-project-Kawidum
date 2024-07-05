<template>
 <br> 
  <v-table>
    <thead>
      <v-expansion-panels>
        <v-expansion-panel :title="props.teamOne + ' vs ' + props.teamTwo">
        </v-expansion-panel>
      </v-expansion-panels>
     
    </thead
  ></v-table>
</template>



<script setup>
const props = defineProps(["teamOne", "teamTwo"]);
let tab=""
</script>
