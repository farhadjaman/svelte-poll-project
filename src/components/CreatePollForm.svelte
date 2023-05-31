<script>
  import Button from "../shared/Button.svelte";
  import {createEventDispatcher} from 'svelte'
  let dispatch=createEventDispatcher();
let fields={
    question:'',
    answerA:'',
    answerB:''
}


const submitHandler=()=>{
     
    //validate question
    if(fields.question.trim()===''){
        alert('Please enter a question')
        return
    }
    //validate answerA
    if(fields.answerA.trim()===''){
        alert('Please enter answer A')
        return
    }
    //validate answerB
    if(fields.answerB.trim()===''){
        alert('Please enter answer B')
        return
    }
    //submit form
    let poll={...fields,votesA:0,votesB:0,id:Math.random()}
    dispatch("addPoll",poll)
    fields.question='';
    fields.answerA='';
    fields.answerB='';
    console.log(poll)
}
</script>

<form action="" on:submit|preventDefault={submitHandler}>
<div class="form-field">
    <label for="question">Poll Questions:</label>
    <input type="text" name="question" id="question" bind:value={fields.question}>
</div>
<div class="form-field">
    <label for="answer-a">Answer A</label>
    <input type="text" name="answer-a" id="answer-a"bind:value={fields.answerA}>
</div>
<div class="form-field">
    <label for="answer-b">Answer B</label>
    <input type="text" name="answer-b" id="answer-b"bind:value={fields.answerB}>
</div>
<div class="button"><Button type='primary' isFlat={true} isInverse={true}>
  Add Poll
</Button></div>

</form>

<style>
  form{
    max-width: 700px;
    margin:0px auto;
    text-align: center;
  }
  .form-field{
    margin-bottom: 16px;
    
  }
  input{
    padding: 8px 16px;
    border-radius: 4px;
    border: 1px solid #ddd;
    width: 100%;
    box-sizing: border-box;
  }
  label{
    display: block;
    margin-bottom: 8px;

  }
  .button{
    
    text-align: left;
  }
  </style>