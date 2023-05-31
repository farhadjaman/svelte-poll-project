<script>
  export let type='primary';
  export let isFlat=false;
  export let isInverse=false;
</script>
<button class={type} class:flat={isFlat} class:inverse={isInverse}>
<slot />
</button>
<style>
   button{
    padding: .5rem 2rem;
    border-radius: 4px;
    border: 0;
    cursor: pointer;
    font-size: 1rem;
    font-weight: 600;
    box-shadow: 1px 2px 3px rgba(0,0,0,.2);
   }
   .primary{
    background-color: #d91b42;
    color: #fff;
   }
    .primary:hover{
      background-color: #b7002d;
    }
    .secondary{
      background-color: #45c496;
    }
    .secondary:hover{
      background-color: #2ea87f;
    }
    .flat{
     box-shadow: none;
    }
    .primary.inverse{
      background-color: #fff;
      color: #d91b42;
      border: 1px solid #d91b42;
    }
    .secondary.inverse{
      background-color: #fff;
      color: #45c496;
      border: 1px solid #45c496;
    }
    
</style>