<script>
  import Button from "../components/Button.svelte";
  import Input from "../components/Input.svelte";
  import A from "../components/A.svelte";
  import {userbaseStore,userStore,promiseStore} from '../stores';



  let username,email,password;

  function signup() {
    $promiseStore = $userbaseStore.signUp({username,password,email})
    .then((user) => {
      $userStore = user
    })
  }

  $: console.log($userStore)
</script>

<form on:submit|preventDefault={signup} class="lg:w-2/6 md:w-1/2 bg-gray-100 rounded-lg p-8 flex flex-col  w-full mt-10 md:mt-0">
  <div class="flex justify-between">
<h2 class="text-gray-900 text-lg font-medium title-font mb-5">Sign Up</h2>
<A href="/#/signin">Or... Sign In</A>
</div> 
  <Input label="Username" bind:value={username} type="text" required/>
   <Input label="Password" bind:value={password} type="password" required/>
   <Input label="Email" bind:value={email} type="email" required/>
   <Button>Sign Up!</Button>
   
    
</form>