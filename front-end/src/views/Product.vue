<template>
<div class="page">
  <div class="menu">
        <router-link to="/"><button>Return to Home</button></router-link>
        <!--<router-link :key="Math.floor(Math.random(1) * 20)" :to="'/product/' + Math.floor(Math.random(1) * 20)"><button>Visit a Random Dog</button></router-link>-->
  </div>
  <div class="image">
    <img class="Dog-Image" :src="'/images/Dog_Pics/'+product.image">
  </div>
  <div class="info">
    <p>Name: {{product.name}}</p>
    <button v-on:click="EditName()">Edit</button>
    <textarea v-model="editName" ></textarea>
  </div>
  <div class="info">
    <p>Age: {{product.age}}</p>
    <button v-on:click="EditAge()">Edit</button>
    <textarea v-model="editAge" ></textarea>
  </div>
  <div class="info">
    <p>Breed: {{product.breed}}</p>
    <button v-on:click="EditBreed()">Edit</button>
    <textarea v-model="editBreed" ></textarea>
  </div>
  <div class = "comments">
  <h3>Add a Comment</h3>
        <input v-model="addedName" placeholder="Name">
        <br />
        <textarea v-model="addedComment" ></textarea>
        <br />
        <button type="submit" v-on:click = "addComment()">Comment</button>
  </div>
  <h2>Comments</h2>
  <div class="comments" v-for="(comment, index) in comments" :key = "index">
      <hr>
        <p>{{comment.text}}</p>
        <p><i>-- {{comment.name}}</i></p>
        <button v-on:click="DeleteComment(index)">DELETE</button>
  </div>
</div>
</template>
<script>

export default {
  name: 'Home',
  data() {
    return {
      product: {},
      editName: "",
      editAge: "",
      editBreed: "",
      addedComment: "",
      addedName: "",
    }
  },
  created() {
    this.product = this.$root.$data.products.find(product => product.id === parseInt(this.$route.params.id));
  },
  methods: {
  addComment()
  {
    let comment = {name:this.addedName, text:this.addedComment, product:this.product}
    console.log(comment);
    this.$root.$data.comments.push(comment);
    this.addedName = "";
    this.addedComment = "";
    this.product = "";
    this.product = this.$root.$data.products.find(product => product.id === parseInt(this.$route.params.id));
  },
  DeleteComment(index)
  {
    this.$root.$data.comments.splice(index,1);
  },
  EditBreed()
  {
    this.product.breed = this.editBreed;
    this.editBreed = "";
  },
  EditAge()
  {
    this.product.age = this.editAge;
    this.editAge = "";
  },
  EditName()
  {
    this.product.name = this.editName;
    this.editName = "";
  },



},
computed: {
  comments()
  {
    console.log(this.product.id)
    return this.$root.$data.comments.filter(comment => comment.product.id === this.product.id);
  }


}
}
</script>
<style scoped>

 .Dog-Image {
  border: 2px solid #333;
  height: 500px;
  width: 800px;
}

.image {
  display: flex;
  align-items: center;
  justify-content: center;
}
.menu {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-bottom: 20px
}
.info {
  display: flex;
  align-items: center;
  justify-content: center;
}
p {
  margin: 20px
}
.comments {
  text-align: center;
}
.page
{
  text-align: center;
}
</style>
