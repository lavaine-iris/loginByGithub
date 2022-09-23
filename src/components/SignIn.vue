<script setup>
  defineProps({
    msg: {
      type: String,
      required: true
    }
  })
  
  supabase.auth.onAuthStateChange((event, session) => { 
  if(session==null){ 
    document.getElementById('status').innerHTML='You are not logged !!!'; 
  } else{ 
    //alert('session value: ' + JSON.stringify(session)) 
    document.getElementById('status').innerHTML='You are logged with the email: ' + session.user.email; 
  } 
})
  </script>
  
  <template>
  <h1>{{ msg }}</h1> 
  <p> 
    Please login if you have an account or register : 
  </p> 
  <button @click="login()">Sign In</button><br> 
  <button @click="logout()">Sign Out</button><br> 
  <label id="status">You are not yet logged !  </label> 
  </template>
  
  <style scoped>
  h1 {
    font-weight: 500;
    font-size: 2.6rem;
    top: -10px;
  }
  
  h3 {
    font-size: 1.2rem;
  }
  
  .greetings h1,
  .greetings h3 {
    text-align: center;
  }
  
  @media (min-width: 1024px) {
    .greetings h1,
    .greetings h3 {
      text-align: left;
    }
  }
  </style>
  