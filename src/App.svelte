<script>
  let userInput = "";
  let quote = "";

  const minNumber = 1;
  const maxNumber = 100;

  const quotes = {
    1: "The greatest glory in living lies not in never falling, but in rising every time we fall. -Nelson Mandela",
    2: "The way to get started is to quit talking and begin doing. -Walt Disney",
    3: "Your time is limited, don’t waste it living someone else’s life. -Steve Jobs",
    // add more quotes as desired
  };

  function handleSubmit() {
    if (userInput >= minNumber && userInput <= maxNumber) {
      quote = quotes[userInput];
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

  <div class="h-20 text-3xl">
    {#if quote}
      <blockquote>
        {quote}
        <footer>
          <cite>- Phasellus eget lacinia</cite>
        </footer>
      </blockquote>
    {/if}
  </div>
</div>
