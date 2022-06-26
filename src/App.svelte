<script>
  let title = "Welcome to calculator";

  let x = 10;
  let y = 11;
  let result = 0;

  let operations = [
    { name: "xor (^)", func: (a,b) => a ^ b },
    { name: "add (+)",  func: (a,b) => a + b },
    { name: "sub (-)",  func: (a,b) => a - b },
    { name: "mod (%)",  func: (a,b) => a % b },
    { name: "rsh (>>)", func: (a,b) => a >> b },
    { name: "lsh (<<)", func: (a,b) => a << b },
    { name: "and (&)",  func: (a,b) => a & b },
    { name: "or  (|)",  func: (a,b) => a | b },
  ];

  let selectedOp = operations[0];

  $: result = selectedOp.func(Number(x), Number(y));

</script>

<main>
  <h2>{title}</h2>

  <label for=""> X : </label> 
  <input type="text" bind:value={x} />

  <select name="operation" id="" bind:value={selectedOp}>
    {#each operations as op}
      <option value={op}>{op.name}</option>
    {/each}
  </select>


  <label for=""> Y : </label> 
  <input type="text" bind:value={y} /><span id="res">  =  {result}
  </span>
</main>

<style>
  input {
    width: 30px;
  }

  * {
    font-family: -apple-system,system-ui,BlinkMacSystemFont,"Segoe UI",Roboto,Oxygen,Ubuntu,"Helvetica Neue",Arial,sans-serif;
  }

  #res:hover {
    background: #ffe100;
  }
</style>
