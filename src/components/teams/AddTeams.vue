<template>
  <section>
    <base-card>
      <h2>What teams are we planning to run?</h2>
      <form @submit.prevent="addTeamComposion">
        <div class="form-wrapper">
          <div class="form-group">
            <h3>Player 1</h3>
            <input
              type="text"
              name="dpsOne"
              placeholder="Player 1 nickname..."
              v-model.trim="p1Nickname"
            />
            <input
              type="text"
              name="class1"
              placeholder="Class"
              v-model="p1Class"
            />
          </div>
          <div class="form-group">
            <h3>Player 2</h3>
            <input
              type="text"
              name="dpsOne"
              placeholder="Player 2 nickname..."
              v-model.trim="p2Nickname"
            />
            <input
              type="text"
              name="class2"
              placeholder="Class"
              v-model="p2Class"
            />
          </div>
          <div class="form-group">
            <h3>Player 3</h3>
            <input
              type="text"
              name="dpsOne"
              placeholder="Player 3 nickname..."
              v-model.trim="p3Nickname"
            />
            <input
              type="text"
              name="class3"
              placeholder="Class"
              v-model="p3Class"
            />
          </div>
          <div class="form-group">
            <h3>Support</h3>
            <input
              type="text"
              name="dpsOne"
              placeholder="Support Nickname..."
              v-model.trim="sNickname"
            />
            <input
              type="text"
              name="sclass"
              placeholder="Class"
              v-model="sclass"
            />
          </div>
        </div>
        <div class="btn-wrapper">
          <base-button>Add Team Composion</base-button>
        </div>
      </form>
    </base-card>
  </section>
</template>
<script>
export default {
  data() {
    return {
      p1Nickname: "",
      p1Class: "",
      p2Nickname: "",
      p2Class: "",
      p3Nickname: "",
      p3Class: "",
      sNickname: "",
      sclass: "",
    };
  },
  methods: {
    addTeamComposion() {
      fetch(
        "https://la4manteamcomp-default-rtdb.firebaseio.com/fourManTeamcomp.json",
        {
          method: "POST",
          headers: {
            "Content-Type": "application/json",
          },
          body: JSON.stringify({
            playerOneNickname: this.p1Nickname,
            playerOneClass: this.p1Class,
            playerTwoNickname: this.p2Nickname,
            playerTwoClass: this.p2Class,
            playerThreeNickname: this.p3Nickname,
            playerThreeClass: this.p3Class,
            supportNickname: this.sNickname,
            supportClass: this.sclass,
          }),
        }
      );

      this.p1Nickname = "";
      this.p1Class = "";
      this.p2Nickname = "";
      this.p2Class = "";
      this.p3Nickname = "";
      this.p3Class = "";
      this.sNickname = "";
      this.sclass = "";
    },
  },
};
</script>

<style scoped>
h2,
h3 {
  text-align: center;
}
form {
  margin-top: 1rem;
}
.form-group {
  padding: 0.5rem;
  border-radius: 1rem;
  border: 3px solid #b91daf;
}
.form-wrapper {
  display: flex;
  justify-content: center;
  gap: 1rem;
}

.form-group input {
  display: block;
  margin: 0.2rem 0;
  padding-left: 0.2rem;
  outline: none;
}
.btn-wrapper {
  display: flex;
  justify-content: center;
  margin-top: 2rem;
}
</style>
