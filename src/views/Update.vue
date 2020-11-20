<template>
  <div class="update_box">
    <h1>Update</h1>
    <form>
        <input type="text" v-model="list.title" placeholder="Type a description here" required/>
        <input type="text" v-model="list.category" placeholder="Type a description here" required/>
        <input type="text" v-for="po in list.point" :key="po" v-model="list.point.po" placeholder="Type a description here" required/>
        <button type="button" class="save" v-on:click="savePoint">Save</button> 
        <button type="button" v-on:click="updatePost">Update post</button>
    </form>
  </div>
</template>

<script>
import { postRef } from "../firebase-db";
export default {
  name: "Update",
  data() {
        return {
           lists : []
        }
    },
  props: {
    list: Object
  },
  methods: {
    updatePost() {
      postRef.doc(this.list.id).set({
        title: this.list.title,
        category: this.list.category,
        point: this.list.point.po
      });

      this.$router.push("/");
    },
    savePoint() {
            this.list.point.set(this.newPoint);
            this.newPoint = "";
        }
  }
};
</script>

<style scoped>
form {
    display: flex;
    flex-direction: column;
    width: 80%;
    margin: 10% auto 0 auto;
    align-items: center;
    background-color: white;
    padding: 30px;
    border-radius: 12px;
    -webkit-box-shadow: 0px 3px 6px 0px rgba(0,0,0,0.28);
    -moz-box-shadow: 0px 3px 6px 0px rgba(0,0,0,0.28);
    box-shadow: 0px 3px 6px 0px rgba(0,0,0,0.28);
    opacity: 95%;
}

button {
    border: none;
    background-color: #FEAD34;
    color: white;
    padding: 10px;
    border-radius: 12px;
    font-size: 20px;
    margin-top: 30px;
    width: 50%;
    outline: none;
}

input {
    border: none;
    height: 20px;
    border-radius: 12px;
    padding: 10px;
    outline: none;
    width: 100%;
    margin: 5px;
    font-size: 14px;
    background-color: #ececec;
}
</style>
