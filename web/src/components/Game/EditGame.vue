<template>
  <div>
<!-- set heading style -->  
    <h1 style="color:blue"><u>Edit Game</u></h1>
    <br>
<!-- set edit form -->      
    <form @submit.prevent="updateGame">
      <div class="row">
        <div class="col-md-12">
          <div class="form-group">
            <label>Platform:</label>
            <input type="text" class="form-control" v-model="game.platform" placeholder="Enter platform">
          </div>
        </div>
        </div>
       <div class="row">       
        <div class="col-md-12">
          <div class="form-group">
            <label>Name:</label>
            <input type="text" class="form-control" v-model="game.name" placeholder="Enter name">
          </div>
        </div>
        </div>
       <div class="row">  
        <div class="col-md-12">
          <div class="form-group">
            <label>Creator:</label>
            <input type="text" class="form-control" v-model="game.creator" placeholder="Enter creator">
          </div>
        </div>
        </div>
       <div class="row">  
        <div class="col-md-12">
          <div class="form-group">
            <label>Development Tool:</label>
            <input type="text" class="form-control" v-model="game.developTool" placeholder="Enter development tool">
          </div>
        </div>
        </div>
       <div class="row">  
        <div class="col-md-12">
          <div class="form-group">
            <label>Description:</label>
            <input type="text" class="form-control" v-model="game.description" placeholder="Enter description">
          </div>
        </div>
        </div>
       <div class="row">  
        <div class="col-md-12">
          <div class="form-group">
            <label>Web Site:</label>
            <input type="text" class="form-control" v-model="game.mode" placeholder="Enter mode">
          </div>
        </div>
        </div>        
       <div class="row">  
        <div class="col-md-12">
          <div class="form-group">
            <label>Language:</label>
            <input type="text" class="form-control" v-model="game.language" placeholder="Enter language">
          </div>
        </div>
        </div>
       <div class="row">          
        <div class="col-md-12">
          <div class="form-group">
            <label>Genre:</label>
            <input type="text" class="form-control" v-model="game.genre" placeholder="Enter genre">
          </div>
        </div>
        </div><br />
        <div class="form-group">
          <button class="btn btn-primary" @click.prevent="updateGame()">Update</button>
        </div>
    </form>
  </div>
</template>

<script>
   
    export default {
      data() {
        return {
          game: {}
        }
      },
      created() {
// get data from uri to create page        
        let uri = `http://localhost:3000/api/editGame/${this.$route.params.id}`;
        this.axios.get(uri).then((response) => { 
          this.game = response.data;  
        })      
      },
      methods: {
        updateGame() {
// post data to uri to update record
          let uri = `http://localhost:3000/api/updateGame/${this.$route.params.id}`;
          this.axios.put(uri, this.game).then(() => {
            this.$message({
                type: 'success',
                message: 'Edit succeeded.'
            })  
// redirect to game list page after record update
            this.$router.push({name: 'games'});
          });
        }
      }
    }
</script>