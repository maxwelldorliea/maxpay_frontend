<script>
  import DateTime from '$lib/components/DateTime.svelte';

  export let data;
</script>

<h1 class="text-center text-4xl mb-4 mt-4">Transaction History</h1>
{#if data.obj.length === 0}
  <div class="flex flex-col h-screen justify-center p-8 text-center">
    <h1 class="text-slate-900 text-4xl dark:text-white">You have not do any transaction</h1>
  </div>
{/if}
{#each data.obj as obj (obj.id)}
  <a href="/transactions/{obj.id}" class="block bg-slate-200 mt-2 mb-2 p-4 rounded-xl">
    <div class="flex justify-between">
      <h2 class="text-2xl">{obj.action}</h2>
      <h3>{(obj.action === "Transfer") ? "To" : "From"}: {obj.receiver_sender_acc_id}</h3>
    </div>
    <div class="flex justify-between">
      <h3>Amount: {obj.amount}</h3>
      <h3><DateTime date={obj.created_at} /></h3>
    </div>
  </a>
{/each}

<style lang="postcss">
</style>
