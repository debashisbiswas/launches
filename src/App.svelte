<script lang="ts">
  import { fly } from "svelte/transition";
  import { quotes } from "./lib/quotes";

  let userInput = "";
  let quote: typeof quotes[number];

  const [minNumber, maxNumber] = [1, quotes.length];

  function handleSubmit() {
    let selection = +userInput;

    if (selection >= minNumber && selection <= maxNumber) {
      const newQuote = quotes[selection - 1];
      if (quote != newQuote) {
        quote = newQuote;
      }
    }
  }
</script>

<div
  class="text-center h-screen w-screen bg-gray-900 text-white grid place-content-center p-4"
>
  <h1 class="text-5xl font-bold tracking-tight mb-8">Launches</h1>

  <form on:submit|preventDefault={handleSubmit} class="mb-16">
    <div class="mb-6">
      <label for="numberField" class="block mb-2 font-medium text-gray-300"
        >Enter a number between {minNumber} and {maxNumber}</label
      >
      <input
        type="number"
        min={minNumber}
        max={maxNumber}
        bind:value={userInput}
        on:input={() => (quote = undefined)}
        id="numberField"
        class="w-32 text-lg text-center border rounded-lg p-2.5 bg-gray-700 border-gray-600 placeholder-gray-400 text-white focus:ring-blue-500 focus:border-blue-500"
        required
      />
    </div>

    <button
      type="submit"
      class="text-white focus:ring-4 focus:outline-none font-medium rounded-lg px-5 py-2.5 bg-blue-600 hover:bg-blue-700 focus:ring-blue-800"
      >Launch</button
    >
  </form>

  <div class="h-32 text-3xl tracking-tight">
    {#key quote}
      {#if quote}
        <blockquote in:fly={{ y: -20 }} out:fly={{ y: 20 }}>
          {quote[0]}
          <footer class="text-gray-400 my-1">
            <cite>- {quote[1]}</cite>
          </footer>
        </blockquote>
      {/if}
    {/key}
  </div>
</div>
