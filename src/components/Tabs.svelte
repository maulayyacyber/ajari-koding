<script>
  import TabIcon from "./TabIcon.svelte";
  import { createEventDispatcher } from "svelte";
  import { FILTERS } from "../constant.js";
  export let activeFilter;

  const dispatch = createEventDispatcher();

  function doFilter(e, filterBy) {
    e.preventDefault();
    dispatch("filter", {
      text: filterBy
    });
  }
</script>

<style>

</style>

<ul class="nav nav-tabs mb-5">
  {#each FILTERS as f (f)}
    {#if f === activeFilter}
      <li class="nav-item">
        <a
          class="nav-link text-capitalize active d-flex align-items-center"
          aria-current="page"
          href="?"
          on:click={e => doFilter(e, f)}>
          <TabIcon {f} />
          <span class="ml-2">{f}</span>
        </a>
      </li>
    {:else}
      <li class="nav-item">
        <a
          class="nav-link text-capitalize d-flex align-items-center"
          href="?tipe={f}"
          on:click={e => doFilter(e, f)}>
          <TabIcon {f} />
          <span class="ml-2">{f}</span>
        </a>
      </li>
    {/if}
  {/each}
</ul>
