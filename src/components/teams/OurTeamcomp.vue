<template>
  <section>
    <div>Name <span>Class</span></div>
    <div>
      {{ p1Nickname }}<span class="dps">{{ p1Class }}</span>
    </div>
    <div>
      {{ p2Nickname }}<span class="dps">{{ p2Class }}</span>
    </div>
    <div>
      {{ p3Nickname }}<span class="dps">{{ p3Class }}</span>
    </div>
    <div>
      {{ sNickname }}
      <span class="sup">{{ sClass }} </span>
    </div>
  </section>
</template>

<script>
export default {
  props: [
    "p1Nickname",
    "p1Class",
    "p2Nickname",
    "p2Class",
    "p3Nickname",
    "p3Class",
    "sNickname",
    "sClass",
  ],
};
</script>

<style scoped>
section {
  margin: 1rem 0;
  border: 1px solid #ccc;
  padding: 1rem;
  border-radius: 12px;
}
div {
  display: flex;
  gap: 3rem;
  justify-content: space-between;
  margin: 0.2rem 0;
}
div:first-child {
  font-weight: bold;
}
span {
  text-align: left;
}

.dps {
  color: red;
}
.sup {
  color: green;
}
</style>
