<script>
  import CurrencyConverter from './CurrencyConverter.svelte';
</script>

<style>
  main {
    font-family: 'Helvetica Neue', Arial, sans-serif;
    text-align: center;
    color: #007BFF;
    max-width: 600px;
    margin: 40px auto;
    padding: 20px;
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
  }

  h1 {
    color: #007BFF;
    margin-bottom: 20px;
  }

  .converter-container {
    display: flex;
    justify-content: center;
    gap: 10px;
    margin-bottom: 20px;
  }

  select, input {
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 16px;
  }

  p {
    font-size: 18px;
    font-weight: bold;
  }
</style>

<main>
  <h1>Currency Converter</h1>
  <CurrencyConverter />
</main>
