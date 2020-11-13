<template>
  <div id="container-fluid">
    <nav class="navbar navbar-dark bg-dark">
      <span class="navbar-text">
            Participants list
      </span>
    </nav>
    <form>
      <h1>Add participants</h1>
      <div class="form-group">
        <label for="participant-name">Name</label>
        <input class="form-control" id="participant-name" placeholder="Enter name" v-model="newParticipantName">
      </div>
      <div class="form-group">
        <label for="participant-last-name">Last name</label>
        <input class="form-control" id="participant-last-name"  placeholder="Enter last name" v-model="newParticipantLastName">
      </div>
      <button type="submit" class="btn btn-primary" v-on:click.prevent="addParticipant()">Submit</button>
    </form>
	    <h1>List</h1>
    <div v-if="participants.length > 0">
        <div v-for="participant in participants" :key="participant.name">{{ participant.name}} {{ participant.lastName}}
	          <button type="submit" class="btn btn-primary" v-on:click.prevent="deleteParticipant(participant)">Delete</button>
		</div>
    </div>
    <div v-else class="alert alert-dark" role="alert">
      No participants yet!
    </div>
	
</div>



  </div>
  
</template>


<script>
export default{
  data: function (){
    return {
      participants: [],
      newParticipantName: null,
      newParticipantLastName: null,
    }
  }, 
  methods: {
    addParticipant: function(){
      var newParticipant = { name: this.newParticipantName, lastName: this.newParticipantLastName };
	  newParticipant.id = Math.random();
      this.participants.push(newParticipant);
      this.newParticipantName = null;
      this.newParticipantLastName = null;
    },
	   deleteParticipant: function(participant){
      this.participants = this.participants.filter((added) => added.id !== participant.id);
    }

  }
}

</script>

<style>
  .container-fluid {
	margin:0;
	padding:0
   }
  .form-group {
  margin: 10px;
  background-color: powderblue;
  }
</style>
