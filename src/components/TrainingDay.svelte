<script>
  import TraininDayDetails from "./TrainingDayDetails.svelte";
  const nbOfDays = [
    { id: 1, text: "One day", value: [1] },
    { id: 2, text: "Two days", value: [1, 2] },
    { id: 3, text: "Three days", value: [1, 2, 3] },
    { id: 4, text: "Four days", value: [1, 2, 3, 4] },
    { id: 5, text: "Five days", value: [1, 2, 3, 4, 5] },
    { id: 6, text: "Six days", value: [1, 2, 3, 4, 5, 6] },
    { id: 7, text: "Seven days", value: [1, 2, 3, 4, 5, 6, 7] }
  ];

  let nbDaysTrainingPerWeek;
</script>

<style>

</style>

<div>
  <form>
    <select bind:value={nbDaysTrainingPerWeek}>
      {#each nbOfDays as day (day.id)}
        <option value={day}>{day.text} per week</option>
      {/each}
    </select>
  </form>
  {JSON.stringify(nbDaysTrainingPerWeek)}
</div>

{#if nbDaysTrainingPerWeek}
  <div>
    {#each nbDaysTrainingPerWeek.value as dayNumber, i}
      <div>
        <TraininDayDetails title={`day ${++i}`} />
      </div>
    {/each}
  </div>
{/if}
