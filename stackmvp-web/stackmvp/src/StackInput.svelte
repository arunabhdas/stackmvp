<script>
  import { createEventDispatcher} from 'svelte';
  const dispatch = createEventDispatcher();
  let title = "";
  let rating = 1;

  const onTitleChange = e => {
    title = e.target.value;
  }

  const onRatingSelect = e => {
    rating = e.target.value;
  }

  const submitStack = () => {
    if (title) {
      dispatch('submitStack', {
        stack: {
          title,
          rating,
        }
      });
      title = '';
      rating = 1;
    }
  }

</script>
<input placeholder="Stack Title" 
type="text"
value={title}
on:keyup={onTitleChange}
/>

<!-- svelte-ignore a11y-no-onchange -->
<select value={rating} on:change={onRatingSelect}>
  <option value={1}>1</option>
  <option value={2}>2</option>
  <option value={3}>3</option>
  <option value={4}>4</option>
  <option value={5}>5</option>

</select>

<button disabled={!title} on:click={submitStack}>Submit</button>