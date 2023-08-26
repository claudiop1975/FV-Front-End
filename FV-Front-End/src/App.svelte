//ESTE COMPONENTE SERÁ EL PRIMERO EN RENDERIZARSE Y CONTENDRÁ UN FORM PARA LOGIN DE 
// USUARIO Y CONTRASEÑA, ESTE SE COMPARARÁ CON LOS GUARDADOS EN UNA BASE DE DATOS, Y 
// SI ES CORRECTO, DEPENDIENDO DEL USER, NOS LLEVARÁ A UNA PÁGINA U OTRA
// DEPENDIENDO SI ES ADMIN, EMPLOYEE, STORE MANAGER O SUPERADMIN
<script>
  let inputUser="";
  let inputPassword="";
  function handleInputUser(event) {
    const input= event.target
    inputUser = input.value
  }
  function handleInputPass(event) {
    const input= event.target
    inputPassword = input.value
  }
  function handleChangeUser(event) {
    console.log(event.target.value);
  }
  function handdleChangePass(event) {
    console.log(event.target.value);
  }
  
  function handleClick(event) {
    function formValidation (inputUser, inputPassword) {
      if (inputUser.length === 0 || inputPassword.length === 0) {
        alert('Por favor, rellene todos los campos');
        return false;
      }
      if (inputUser.length < 6 || inputPassword.length < 6) {
        alert('El usuario y la contraseña deben tener al menos 6 caracteres');
        return false;
      }
      if (inputUser !== RegExp(/^[a-zA-Z0-9]+$/)) {
        alert('El usuario solo puede contener letras y números');
        return false;
      }
      if (inputPassword !== RegExp(/^[a-zA-Z0-9]+$/)) {
        alert('La contraseña solo puede contener letras y números');
        return false;
      }
      return true;
    }
      event.preventDefault();
      
    }
  
  


    // import { onMount } from 'svelte';
    // import { navigate } from 'svelte-routing';
    // import { get } from 'svelte/store';
    // import { user } from './store.js';
    // import { getCookie } from './utils.js';

    // onMount(() => {
    //     const token = getCookie('token');
    //     if (token) {
    //         user.set(token);
    //         navigate('/dashboard');
    //     }
    // });
</script>
<main class="title">
    <h1>FV DELIVERY'S</h1>
    <form class="forms">
        <input  
          type="text" placeholder="Usuario" 
          on:change={handleChangeUser}
          on:keyup={handleInputUser}>
            {#if inputUser.length === 0}
            <p class="pInput">El usuario no puede estar vacío</p>
            {/if}
        <input
          type="password" placeholder="Contraseña" 
          on:change={handdleChangePass}
          on:keyup={handleInputPass}>
            {#if inputPassword.length === 0}
            <p class="pInput">La contraseña no puede estar vacía</p>
            {/if}
        <button type="submit"
        disabled={inputUser.length!==0 || inputPassword.length === 0}
        on:click={handleClick} 
        >Bienvenido {inputUser}</button>
    </form>

</main>

<style>
    .title {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 1em;
    }
    .pInput {
        color: red;
        font-size: 0.8em;
    }
    .forms {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        gap: 1em;
    }
    input {
        width: 20em;
        height: 2em;
        border-radius: 1em;
        border: none;
        padding: 0 1em;
    }
    button {
        width: 10em;
        height: 3em;
        border-radius: 1em;
        border: none;
        background-color: #646cff;
        color: white;
        font-weight: bold;
        cursor: pointer;
    }
    button:hover {
        background-color: #ff3e00;
    }

</style>




















<!-- <script>
  import svelteLogo from './assets/svelte.svg'
  import viteLogo from '/vite.svg'
  import Counter from './lib/Counter.svelte'
</script>

<main>
  <div>
    <a href="https://vitejs.dev" target="_blank" rel="noreferrer">
      <img src={viteLogo} class="logo" alt="Vite Logo" />
    </a>
    <a href="https://svelte.dev" target="_blank" rel="noreferrer">
      <img src={svelteLogo} class="logo svelte" alt="Svelte Logo" />
    </a>
  </div>
  <h1>Vite + Svelte</h1>

  <div class="card">
    <Counter />
  </div>

  <p>
    Check out <a href="https://github.com/sveltejs/kit#readme" target="_blank" rel="noreferrer">SvelteKit</a>, the official Svelte app framework powered by Vite!
  </p>

  <p class="read-the-docs">
    Click on the Vite and Svelte logos to learn more
  </p>
</main>

<style>
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
  .read-the-docs {
    color: #888;
  }
</style> -->
