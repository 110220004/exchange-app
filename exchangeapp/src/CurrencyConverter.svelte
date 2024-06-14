<script>
    import { onMount } from 'svelte';
    let rates = {};
    let amount = 1;
    let selectedCurrency = 'EUR';
    let baseCurrency = 'USD';
  
    async function fetchRates() {
      const response = await fetch(`https://open.er-api.com/v6/latest/${baseCurrency}`);
      const data = await response.json();
      rates = data.rates;
    }
  
    onMount(fetchRates);
  
    $: convertedAmount = amount * rates[selectedCurrency];
    $: if (baseCurrency !== selectedCurrency) fetchRates();
  </script>
  
  <style>
    .currency-inputs {
      display: flex;
      align-items: center;
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
  
  <div class="currency-inputs">
    <select bind:value={baseCurrency} on:change={fetchRates}>
      {#each Object.keys(rates) as currency}
        <option>{currency}</option>
      {/each}
    </select>
    <input type="number" bind:value={amount} min="0" step="0.01">
  </div>
  <select bind:value={selectedCurrency}>
    {#each Object.keys(rates) as currency}
      <option>{currency}</option>
    {/each}
  </select>
  <p>{amount} {baseCurrency} = {convertedAmount} {selectedCurrency}</p>
  