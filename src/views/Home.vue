<template>
  <div class="container">
    <section class="vote">
      <h3 class="give-your-vote">
        Silahkan berikan penilaian anda terhadap pelayanan kami
      </h3>

      <div class="emoticons">
        <vote/>
      </div>
    </section>

      <section class="finish">
        <h4>Terima kasih telah memberikan penilaian anda</h4>
      </section>
  </div>
</template>

<script>
// @ is an alias to /src
import vote from "@/components/vote.vue";

export default {
  name: "Home",
  components: { vote }
};
</script>

<style type="text/css">
  .container{
    display: flex;
    flex-wrap: wrap;
    height: 100vh;
    align-items: center;
  }

  section{
    width: 100%;
  }

  .emoticons{
    display: flex;
    justify-content: center;
  }
</style>