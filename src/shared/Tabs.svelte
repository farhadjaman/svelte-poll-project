<script>
export let items;
export let activeItem;
import { createEventDispatcher } from "svelte";

const dispatch=createEventDispatcher();
</script>

<div class="tabs">
  <ul>

    {#each items as item}
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <li on:click={()=>dispatch('tabChange',item)}>
      <div class:active={item===activeItem}>{item}</div>
    </li>
    {/each}
  </ul>
</div>

<style>
  .tabs {
    margin-bottom: 40px;
  }
  ul{
    display: flex;
    padding: 0;
    justify-content: center;
 
    list-style: none;
  }
  li{
    margin: 0 16px;
    font-size: 1rem;
    color:#555;
    cursor: pointer;
  }
  .active {
    color: #d91b42;
    border-bottom: 2px solid #d91b42;
    padding-bottom: 8px;
  }
</style>