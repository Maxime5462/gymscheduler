<script>
  export let title;
  let exercise = {
    activity: "",
    sets: 4,
    reps: 10
  };

  let exercises = [];

  function handleSubmit() {
    exercises = [...exercises, { ...exercise }];
    console.log("exercises", exercises);
  }
</script>

<div>
  <h2>{title}</h2>
  <div>
    <form on:submit|preventDefault={handleSubmit}>
      <div>
        <label for="activity">Activity</label>
        <input type="text" id="activity" bind:value={exercise.activity} />
      </div>
      <div>
        <label for="sets">Sets</label>
        <input type="number" id="sets" bind:value={exercise.sets} />
      </div>
      <div>
        <label for="reps">Reps</label>
        <input type="number" id="reps" bind:value={exercise.reps} />
      </div>
      <button type="submit">add exercise</button>
    </form>
  </div>
</div>
