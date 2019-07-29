<script>
  import JobItem from "./JobItem.svelte";
  export let jobs;
</script>

<style>
  section {
    width: 100%;
    display: grid;
    grid-template-columns: 1fr;
    grid-gap: 1rem;
  }

  @media (min-width: 768px) {
    section {
      grid-template-columns: repeat(2, 1fr);
    }
  }
</style>

<section id="jobs">
  {#each jobs as job, i (job.id)}
    <JobItem
      id={job.id}
      title={job.title}
      subtitle={job.subtitle}
      description={job.description}
      imageUrl={job.imageUrl}
      address={job.address}
      contactEmail={job.contactEmail}
      on:togglefavorite />
  {/each}
</section>
