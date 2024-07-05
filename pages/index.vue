<template>

  <v-container class="fill-height">
    <v-row no-gutters>
      <v-col cols="12" md="12" lg="12" sm="12">
        <h1>UEFA EURO 2024</h1>
        <v-card>
          <v-tabs v-model="tab" align-tabs="center" color="deep-purple-accent-4">
            <v-tab :value="1">1. Runde Gruppenphase</v-tab>
            <v-tab :value="2">2. Runde Gruppenphase</v-tab>
            <v-tab :value="3">3. Runde Gruppenphase</v-tab>
            <v-tab :value="4">Achtelfinale</v-tab>
            <v-tab :value="5">Viertelfinale</v-tab>
            <v-tab :value="6">Halbfinale</v-tab>
            <v-tab :value="6">Finale</v-tab>
          </v-tabs>

          <v-tabs-window v-model="tab">
            <v-tabs-window-item v-for="n in 3" :key="n" :value="n">
              <v-container fluid>
                <v-row>
                  <v-col v-for="i in 6" :key="i" cols="12" md="4">
                    <v-img
                      :lazy-src="`https://picsum.photos/10/6?image=${
                        i * n * 5 + 10
                      }`"
                      :src="`https://picsum.photos/500/300?image=${
                        i * n * 5 + 10
                      }`"
                      height="205"
                      cover
                    ></v-img>
                  </v-col>
                </v-row>
              </v-container>
            </v-tabs-window-item>
          </v-tabs-window>
        </v-card>
        <my-first-component v-for="match in groups.firstGroupStage" :key="match.matchID" :team-one="match.team1.teamName" :team-two="match.team2.teamName" ></my-first-component>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
const { data } = await useFetch(
  "https://api.openligadb.de/getmatchdata/em/2024/"
);

 let groups = {
   firstGroupStage: [],
   secondGroupStage: [],
   thirdGroupStage: [],
   roundOf16: [],
   roundOf8: [],
   roundOf4: [],
   final: [],
 };
 
 for (const match of data.value) {
   if (match.group.groupName === "1. Runde Gruppenphase") {
     groups.firstGroupStage.push(match)
   }
   if (match.group.groupName === "2. Runde Gruppenphase") {
     groups.secondGroupStage.push(match)
   }
   if (match.group.groupName === "3. Runde Gruppenphase") {
     groups.thirdGroupStage.push(match)
   }
   if (match.group.groupName === "Achtelfinale") {
     groups.roundOf16.push(match)
   }
   if (match.group.groupName === "Viertelfinale") {
     groups.roundOf8.push(match)
   }
   if (match.group.groupName === "Halbfinale") {
     groups.roundOf4.push(match)
   }
   if (match.group.groupName === "Finale") {
     groups.final.push(match)
   }}
</script>
const props = defineprops ['firstGroupStage','secondGroupStage','thirdGroupStage','roundOf16','roundOf8','roundOf4','final']