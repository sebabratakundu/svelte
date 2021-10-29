<script>
  export let showModal = false;
  export let isPromo = false;
  export let title = "Default Modal";
  export let msg = "Empty!";
</script>

{#if showModal}
<!-- event forwarding & event modifier -->
<div class="backdrop" on:click|self>
  <div class="my-modal" class:promo={isPromo}>
    <div class="my-modal-content">
      <!-- Modal Header -->
      <div class="my-modal-header">
        <h4 class="my-modal-title">{title}</h4>
      </div>
  
      <!-- Modal body -->
  
      <!-- conditional class -->
      <div class="my-modal-body">
        {msg}
      </div>
    </div>
  </div>
</div>
{/if}


<style>
  .backdrop{
    width: 100%;
    height: 100%;
    position : fixed;
    top : 0;
    left : 0;
    background-color: rgba(0, 0, 0, 0.5);
  }

  .my-modal{
    width : 400px;
    padding : 20px;
    background-color: white;
    margin: 50px auto;
  }

  .promo{
    background-color: antiquewhite;
  }
</style>