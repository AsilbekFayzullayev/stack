<template>
  <div>
    <!--    <v-row justify="center" align="center">-->
    <!--      <v-col cols="12" sm="12" md="4">-->
    <!--        <div class="py-2 d-flex">-->
    <!--          <h5 class="categoryFront">FrontEnd</h5>-->
    <!--          <p class="mx-2"></p>-->
    <!--          <h5 class="categoryBack">Backend</h5>-->
    <!--        </div>-->
    <!--      </v-col>-->
    <!--    </v-row>-->
    <div class="d-flex">
      <span style="font-size: 25px">All Questions</span>
      <v-spacer></v-spacer>
      <v-btn class="askQuestionBtn">
        Ask Questions
      </v-btn>
    </div>
    <v-row class="my-5">
      <v-col cols="12" md="6" sm="6">
        <h4 class="my-2">1 900 000 questions</h4>
      </v-col>
      <v-col cols="12" md="6" sm="6">
        <v-select
          label="Search By Category"
          class="selectCategory"
          v-model="value"
          :items="items"
          item-color="#033"
          chips
          dark
          multiple
          dense
          solo
        ></v-select>
      </v-col>
    </v-row>
    <div>
      <v-row class="d-flex mt-5" style="outline: 1px solid black;background-color: black" v-for="item of questions"
             :key="item.id">
        <v-col cols="12" md="2" sm="2" style="width: 10%" class="px-4 py-1 text-center">
          <h4 class="text-center" style="font-size: 12px">Username</h4>
          <img src="https://static.toiimg.com/photo/72975551.cms" width="50" height="50" class="text-center"
               style="border-radius: 50%"/>
          <div style="background-color: #35495e;color: white;border-radius: 10px">
            10
            <p class="text-center pb-0 mb-0" style="font-size: 12px">answers</p>
          </div>
        </v-col>
        <v-col cols="12" sm="10" md="10" style="width: 85%;border-left: 1px solid #3b8070" class="px-4 py-1">
          <NuxtLink :to="`/question/${item.title}`" class="title">{{ item.title }}</NuxtLink>
          <p>{{ item.description }}</p>
          <div>
            <span style="background-color: cornflowerblue; padding: 2px 5px">html</span>
            <span style="background-color: cornflowerblue; padding: 2px 5px">css</span>
          </div>
        </v-col>
      </v-row>
    </div>
  </div>
</template>

<script>
export default {
  data: () => ({
    items: ['html', 'css', 'js', 'vue js', 'react js'],
    value: '',
    questions: [
      {
        userId: "Id",
        id: "1",
        title: "title",
        description: "description ",
        categories: ['html', 'css', '....'],
        code: "",
        answers: [
          {id: "", description: "answer", code: "", isLiked: false, userId: "id"},
          {id: "", description: "answer", code: "", isLiked: false, userId: "id"},
        ]
      }, {
        userId: "Id",
        id: "2",
        title: "title",
        description: "description ",
        categories: ['html', 'css', '....'],
        code: "",
        answers: [
          {id: "", description: "answer", code: "", isLiked: false, userId: "id"},
          {id: "", description: "answer", code: "", isLiked: false, userId: "id"},
        ]
      }
    ],

    user: {
      id: "",
      username: "",
      email: "",
      questions: [],
      answers: [
        {id: "", description: "answer", code: "", isLiked: false, userId: "id"},
      ]
    }
  }),

  watch: {
    value(val) {
      console.log(val)
    }
  }
}
</script>
<style scoped>
.categoryFront {
  width: 50%;
  height: 100%;
  padding: 20px;
  cursor: pointer;
  background-color: black;
  text-align: center;
}

.categoryBack {
  width: 50%;
  padding: 20px;
  cursor: pointer;
  background-color: black;
  text-align: center;
}

.title {
  color: cornflowerblue;
  cursor: pointer;
}

.askQuestionBtn {
  background-color: #35495e !important;
  color: white;
}

.selectCategory {
  color: #35495e;
}
</style>
