<script>
  let userInput = '';
  let quote = '';

  const minNumber = 1;
  const maxNumber = 100;

  const quotes = {
    1: 'The greatest glory in living lies not in never falling, but in rising every time we fall. -Nelson Mandela',
    2: 'The way to get started is to quit talking and begin doing. -Walt Disney',
    3: 'Your time is limited, don’t waste it living someone else’s life. -Steve Jobs',
    // add more quotes as desired
  };

  function handleSubmit() {
    if (userInput >= minNumber && userInput <= maxNumber) {
      quote = quotes[userInput];
    }
  }
</script>

<main>
  <h1>Launches</h1>
  <form on:submit|preventDefault={handleSubmit}>
    <label>
      Enter a number between {minNumber} and {maxNumber}:
    </label>
    <input type="number" min="1" max="100" bind:value={userInput} required />
    <button type="submit">Submit</button>
  </form>
  {#if quote}
    <p>{quote}</p>
  {/if}
</main>

<style>
  form {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 2rem;
  }

  label {
    font-size: 1.2rem;
    margin-bottom: 1rem;
  }

  input {
    padding: 0.5rem;
    font-size: 1.2rem;
    border-radius: 0.25rem;
    border: 1px solid gray;
    text-align: center;
  }

  h1 {
    font-size: 3.2em;
    line-height: 1.1;
  }

  p {
    margin-top: 2rem;
    font-size: 1.5rem;
    font-style: italic;
  }

  button {
    border-radius: 8px;
    border: 1px solid transparent;
    padding: 0.6em 1.2em;
    font-size: 1em;
    font-weight: 500;
    font-family: inherit;
    background-color: #1a1a1a;
    cursor: pointer;
    transition: border-color 0.25s;
    margin: 1rem;
  }

  button:hover {
    border-color: #646cff;
  }

  button:focus,
  button:focus-visible {
    outline: 4px auto -webkit-focus-ring-color;
  }
</style>
