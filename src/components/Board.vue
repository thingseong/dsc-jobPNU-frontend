<template>
  <div>
    <h1>스터디 그룹 모집 목록</h1>
    <v-container grid-list-md>
      <v-data-table :headers="headers" :items="data" @click:row="detail">
      </v-data-table>
      <v-row>
        <v-btn outlined color="blue" @click="write">스터디 생성</v-btn>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import data from "@/data";
export default {
  name: "Board",

  data() {
    return {
      headers: [
        {
          text: "제목",
          value: "title",
          sortable: true
        },
        {
          text: "작성자",
          value: "user",
          sortable: false
        }
      ],
      data: data
    };
  },
  methods: {
    write() {
      this.$router.push({
        path: "create"
      });
    },

    // detail(item) {
    //     this.$router.push('/detail/' + item.id)
    // }

    detail(item) {
      this.$router.push({
        name: "Detail",
        params: {
          contentId: item.id
        }
      });
    }
  },
  mounted() {
    this.$axios.get("/users").then(data => console.log(data));
  }
};
</script>

<style>
h1 {
  text-align: center;
  margin-top: 1em;
}
</style>
