<template>
    <form @submit.prevent="uploadPhoto" action="{{ url_for('upload') }}" method="POST" enctype="multipart/form-data">
        <label>Description</label>
        <input type="text" name="desc">
        <br>
        <label>Photo Upload</label>
        <input type="file" name="photo">
        <br>
        <button type="submit" name="submit" class="btn btn-primary">Upload file</button>
    </form>
</template>

<script>
export default {
  data() {
    return {
      csrf_token: "",
      response: null,
    };
  },
    methods:{
        uploadPhoto() {
            
            fetch("/api/upload", {
                method: 'POST'
            })
            
            .then(function (response) {
                return response.json();
            })
            
            .then(function (data) {
                // display a success message
                console.log(data);
            })
            
            .catch(function (error) {
                console.log(error);
            });
        }

    }
    
</script>