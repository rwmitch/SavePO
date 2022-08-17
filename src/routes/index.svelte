<script lang="ts">
  import axios from "axios";

  const handleSubmit = (e: SubmitEvent) => {
    const formData = new FormData(e.target as HTMLFormElement);
    let contactInfo: Array<Record<string, unknown>>;

    const name = formData.get("name");
    const email = formData.get("email");
    const postcode = formData.get("postcode");

    axios.get("https://members-api.parliament.uk/api/Location/Constituency/Search", {
      params: {
        searchText: postcode,
        take: 1
      }}).then(res => {
        const id = res.data.items[0].value.currentRepresentation.member.value.id;
        axios.get(`https://members-api.parliament.uk/api/Members/${id}/Contact`).then(res2 => {
          contactInfo = res2.data.value;
          
          let parliamentary = contactInfo.find(info => info.type == "Parliamentary");
          let constituency = contactInfo.find(info => info.type == "Constituency");

          let message = `Test\nTest`;
          let mailtoLink = `mailto:${parliamentary?.email}?cc=nick.read1@postoffice.co.uk&subject=Save Our Post Office&body=${message}`
            .replaceAll(" ", "%20").replaceAll("\n", "%0D%0A");

          window.open(mailtoLink);
          console.log(mailtoLink);
        });
      });

  }
</script>

<h1>#SaveYourPO</h1>

<form on:submit|preventDefault={handleSubmit}>
  <label for="name">Your Name</label> <input id="name" name="name" type="text" />
  <label for="email">Your Email</label> <input id="email" name="email" type="email" />
  <label for="postcode">Your Postcode</label> <input id="postcode" name="postcode" type="text" />
  <button type="submit">Submit</button>
</form>

<style>
  form {
    width: 70vw;
    margin: auto;
    padding: 10px;
    background-color: #ccc;
    display: grid;
    grid-template-columns: 25% calc(75% - 10px);
    grid-column-gap: 10px;
    grid-row-gap: 10px;
  }

  label {
    text-align: right;
  }
</style>
