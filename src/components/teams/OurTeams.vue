<template>
  <section>
    <base-card>
      <h2>Our Team Comp</h2>
      <p v-if="isLoading">Loading...</p>
      <p v-else-if="!isLoading && error">{{ error }}</p>
      <p v-else-if="!isLoading && (!teams || teams.length === 0)">
        No Teams Yet maybe add some?
      </p>
      <ul>
        <our-teamcomp
          v-for="team in teams"
          :key="team.id"
          :p1Nickname="team.p1Nickname"
          :p1Class="team.p1Class"
          :p2Nickname="team.p2Nickname"
          :p2Class="team.p2Class"
          :p3Nickname="team.p3Nickname"
          :p3Class="team.p3Class"
          :sNickname="team.sNickname"
          :sClass="team.sClass"
        ></our-teamcomp>
      </ul>
    </base-card>
  </section>
</template>

<script>
import OurTeamcomp from "./OurTeamcomp.vue";
export default {
  components: {
    OurTeamcomp,
  },
  data() {
    return {
      teams: [],
      error: null,
      isLoading: false,
    };
  },
  methods: {
    loadTeams() {
      this.error = null;
      this.isLoading = true;
      fetch(
        "https://la4manteamcomp-default-rtdb.firebaseio.com/fourManTeamcomp.json"
      )
        .then((response) => {
          if (response.ok) {
            return response.json();
          }
        })
        .then((data) => {
          this.isLoading = false;
          const teams = [];
          for (const id in data) {
            teams.push({
              id: id,
              p1Nickname: data[id].playerOneNickname,
              p1Class: data[id].playerOneClass,
              p2Nickname: data[id].playerTwoNickname,
              p2Class: data[id].playerTwoClass,
              p3Nickname: data[id].playerThreeNickname,
              p3Class: data[id].playerThreeClass,
              sNickname: data[id].supportNickname,
              sClass: data[id].supportClass,
            });
          }
          this.teams = teams;
        })
        .catch((error) => {
          this.error = "Failed to fetch data - please try again later";
          this.isLoading = false;
          console.log(error);
        });
    },
  },
  mounted() {
    this.loadTeams();
  },
};
</script>

<style scoped>
h2 {
  text-align: center;
}
ul {
  list-style: none;
  display: flex;
  gap: 2rem;
  flex-wrap: wrap;
}
</style>
