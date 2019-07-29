<script>
  import uid from "uid";
  // components
  import Header from "./UI/Header.svelte";
  import JobGrid from "./Jobs/JobGrid.svelte";
  import TextInput from "./UI/TextInput.svelte";
  import Button from "./UI/Button.svelte";

  let title = "";
  let subtitle = "";
  let address = "";
  let imageUrl = "";
  let contactEmail = "";
  let description = "";
  let isFavorite = false;

  let jobs = [
    {
      id: uid(),
      title: "NDE",
      subtitle: "Offshore Northsea, full ROV team, Windfarm & Renewables",
      description:
        "Offshore windpark inspection project, full summer season 3-6 months work",
      imageUrl:
        "https://strikersoft.com/media/images/Logo_NDE_Offshore_600x195.width-300.jpg",
      address: "NDE Offshore, AB Bäckvägen, 20 192 54 ,Sollentuna, Sweden",
      contactEmail: "info@ndeoffshore.com",
      isFavorite: false
    },
    {
      id: uid(),
      title: "DCN",
      subtitle: "Offshore Gulf of Mexico Pipline repair job",
      description:
        "full team, tie-ins, offshore pipeline repair job Gulf Mexico, 3 month project",
      imageUrl:
        "data:image/png;base64,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",
      address: "Sittarderstrasse 1 D 52525, Heinsberg, Germany",
      contactEmail: "dcndeutschland@aol.com",
      isFavorite: false
    }
  ];

  function addJob() {
    const newJob = {
      id: uid(),
      title: title,
      subtitle: subtitle,
      description: description,
      imageUrl: imageUrl,
      address: address,
      contactEmail: contactEmail
    };

    jobs = [newJob, ...jobs];
    console.log(jobs);
  }

  function handleFavorite(dispatch) {
    console.log("clicked", dispatch.detail);
    let selectedJob = jobs.filter(item => item.id === dispatch.detail);
    selectedJob.isFavorite = selectedJob === false ? true : false;
    console.log(selectedJob);
  }
</script>

<style>
  main {
    margin-top: 5rem;
  }

  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>

<Header />

<main>
  <form on:submit|preventDefault={addJob}>
    <TextInput
      id="title"
      label="Title"
      value={title}
      on:input={event => (title = event.target.value)} />
    <TextInput
      id="subtitle"
      label="Subtitle"
      value={subtitle}
      on:input={event => (subtitle = event.target.value)} />
    <TextInput
      id="address"
      label="Address"
      value={address}
      on:input={event => (address = event.target.value)} />
    <TextInput
      id="imageUrl"
      label="Image URL"
      value={imageUrl}
      on:input={event => (imageUrl = event.target.value)} />
    <TextInput
      id="contactEmail"
      label="Email"
      value={contactEmail}
      type="email"
      on:input={event => (contactEmail = event.target.value)} />
    <TextInput
      id="description"
      label="Description"
      value={description}
      controlType="textarea"
      rows="3"
      on:input={event => (description = event.target.value)} />
    <Button type="submit" caption="Save" />
  </form>
  <JobGrid on:togglefavorite={handleFavorite} {jobs} />
</main>
