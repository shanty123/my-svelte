<script>
    import Button from "../components/Button.svelte";
    import Input from "../components/Input.svelte";
    import {userbaseStore,userStore,promiseStore} from '../stores';
  
  
  
    let username;
  
    function forgotpassword() {
        $promiseStore = $userbaseStore.forgotPassword({username})
      .then((user) => {
        $userStore = user
      })
    }
  
    $: console.log($userStore)
  </script>
  
  <form on:submit|preventDefault={forgotpassword} class="lg:w-2/6 md:w-1/2 bg-gray-100 rounded-lg p-8 flex flex-col  w-full mt-10 md:mt-0">
      <h2 class="text-gray-900 text-lg font-medium title-font mb-5">Forgot Password</h2>
     <Input label="Username" bind:value={username} type="text" required/>
     
     
     <Button>Send Email</Button>
     
      
  </form>