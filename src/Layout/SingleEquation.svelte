<script>
  export let answered;
  export let disabled;
  export let quizQuestion;
  import NumericInputv2 from "../GenericComponents/NumericInputv2.svelte";
  import { INPUT_SYMBOL } from "../quizzes/constants";
  import { fade, fly } from "svelte/transition";
  import { slide } from "svelte/transition";
</script>

<style>
  .wrapper {
    border: 1px solid black;
    /* background-color: white; */
    display: flex;
  }

  .cell {
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 1.5rem;
    margin: 0 0.2rem;
  }

  .input {
    border: 1px solid black;
    border-radius: 2px;
    width: 3rem;
    height: 3rem;
  }

  .symbol {
  }
</style>

<div class="wrapper">
  {#each quizQuestion.getAsArray() as element}
    <div class="cell">
      {#if element === INPUT_SYMBOL && !answered}
        <div class="input">
          <NumericInputv2
            {disabled}
            value={4}
            maxLength={quizQuestion.getCorrectAnswer().length} />

        </div>
      {:else}
        <div class="symbol">{element}</div>
      {/if}
    </div>
  {/each}
</div>
