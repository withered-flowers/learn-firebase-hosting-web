<script>
  import { onMount } from "svelte";

  // initial state
  let dataUsers = [];
  let isFetching = true;

  // onMount lifecycle
  onMount(async () => {
    const response = await fetch("https://jsonplaceholder.typicode.com/users");
    dataUsers = await response.json();

    // when data fetching is done
    isFetching = false;
  });
</script>

{#if isFetching === true}
  Loading data fetcher ...
{:else}
  <table class="table-auto border-2">
    <thead class="border-2 bg-gray-200">
      <tr>
        <th>Id</th>
        <th>Name</th>
        <th>Username</th>
        <th>Email</th>
      </tr>
    </thead>
    <tbody>
      {#each dataUsers as user}
        <tr class="border-2">
          <td class="border-2">{user.id}</td>
          <td class="border-2">{user.name}</td>
          <td class="border-2">{user.username}</td>
          <td class="border-2">{user.email}</td>
        </tr>
      {/each}
    </tbody>
  </table>
{/if}

<style></style>
