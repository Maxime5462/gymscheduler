<script>
  import { onMount } from "svelte";
  export let summary;
  export let days;
  let formattedData;
  let isDataFormatted = false;

  function prepareSummary() {
    // acc looks like { "day 1": [], "day 2": []}
    // curr looks like { activity: 'squat', sets: 4, reps: 12, title 'day 1'}
    formattedData = summary.reduce((acc, curr) => {
      if (Object.keys(acc).includes(curr.title)) {
        acc[curr.title] = [...acc[curr.title], curr];
      } else {
        acc[curr.title] = [curr];
      }
      return acc;
    }, {});
    isDataFormatted = true;
    console.log(formattedData);
  }

  onMount(() => {
    prepareSummary();
  });
</script>

<style>

</style>

<h2>Summary</h2>
{#if isDataFormatted}{formattedData}{/if}
