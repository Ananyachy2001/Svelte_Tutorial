<script>
  import Modal from './Modal.svelte';
let showModal = false;
  let people = [
    { name: "Joy", beltColour: "black", age: 26, id: 1 },
    { name: "Floran", beltColour: "blue", age: 46, id: 2 },
    { name: "Jimmy", beltColour: "red", age: 35, id: 3 },
  ];

  const handleClick = (id) => {
    //delete the person from people
    people = people.filter((person) => person.id != id); //reassign
  };

  const toggleModal = () =>{
    showModal = !showModal;
  }

let num = 7;
</script>
<!-- <Modal message="Hey, i'm a prop value" isPromo={true} /> -->
<Modal message="Default 2 value"  showModal={showModal} on:click={toggleModal}/>
{#if num > 20}
  <p>Greater than 20</p>
{:else if num > 5}
  <p>Greater than 5</p>
{:else}
  <p>Not greater than 5</p>
{/if}
<main>
  <div>
    <button on:click={toggleModal}>Open Modal</button>
    
    {#each people as person (person.id)}
      <div>
        <h4>{person.name}</h4>
        {#if person.beltColour === "black"}
          <p><strong>MASTER NINJA</strong></p>
        {/if}
        <p>{person.age} years old, {person.beltColour} belt.</p>
        <button on:click={() => handleClick(person.id)}>delete</button>
      </div>
    {:else}
      <p>There are no people to show</p>
    {/each}
  </div>
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>
