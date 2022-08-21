<!--<script lang="ts">
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
</style>-->

<svelte:head>
  <link href="https://fonts.googleapis.com/css2?family=Krona+One&family=Roboto:wght@300&display=swap" rel="stylesheet"> 
</svelte:head>

<h1 class="title">#SaveYourPostOffice</h1>
<section class="intro">
  <p>Post Offices across the country are being paid less than minimum wage by Post Office Ltd (POL), leading to the closure of many branches.</p>
  <p>We are no longer paid any salary, our pay is only commission based.</p>
  <b>We have just two simple demands:</b>
</section>
<section class="demands">
  <article class="demand rates">
    <p class="demand-headline">Increase remuneration rates for all transactions</p>
    <p class="demand-explanation">Currently remuneration rates are very low for all transactions. In fact, many transactions have absolutely no remuneration</p>
  </article>
  <article class="demand mains">
    <p class="demand-headline">Pay all branches the same rate as Main branches</p>
    <p class="demand-explanation">Main branches are paid more than Local and Traditional model branches. We believe this is a form of discrimination by POL, and should no longer be tolerated by us.</p>
  </article>
</section>

<style lang="scss">
  :global(body) {
    font-family: Roboto, sans-serif;
    margin: 0;
    font-size: 18px;
  }

  h1.title {
    font-family: 'Krona One', sans-serif;
    text-align: center;
    color: red;
  }

  section.intro {
    width: 70vw;
    margin: 10px auto;
    text-align: center;
  
    b {
      font-size: 24px;
    }
  }

  section.demands {
    display: grid;
    grid-template-columns: repeat(2, 50%);
  }

  article.demand {
    width: calc(100% - 10px);
    padding: 5px;
    text-align: center;
  }

  article.demand.rates {
    background-color: #ff8b8b;
  }

  article.demand.mains {
    background-color: #9fd1ff;
  }

  p.demand-headline {
    font-family: 'Krona One', sans-serif;
  }
</style>
