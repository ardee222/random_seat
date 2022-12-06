<script>
  import data from "./data/data.json"
  let student_data = data;
  let date = new Date();
  let year = date.getFullYear();
  let month = date.getMonth();
  let day = date.getDay();
  function shuffle(){
    for(let i=20;i>1;i--){
      setTimeout(()=>{
      student_data = student_data.sort(() => {return Math.random() - 0.5})
      },i*200)}
  }
  let row1,row2,row3,row4,row5,row6,row7
  $: row1 = student_data.slice(0,5);
  $: row2 = student_data.slice(5,10);
  $: row3 = student_data.slice(10,16);
  $: row4 = student_data.slice(16,22);
  $: row5 = student_data.slice(22,28);
  $: row6 = student_data.slice(28,33);
  $: row7 = student_data.slice(33,39);
  let clicked = false;
  function change_board(){
    clicked = !clicked;
    let board = clicked ? "其實我叫黑板" : "綠板"
    document.getElementsByName('black_board')[0].innerText = board;
  }
</script>

<main class="max-w-md w-full max-h-screen h-screen bg-slate-700 mx-auto flex flex-col">
  <div class="relative m-4">
    <div class="absolute top-0 right-0 text-white font-serif text-xs">{year}年{month}月{day}日</div>
  </div>
  <div name="container" class="flex my-8 h-72 mx-auto font-serif border px-4 py-8 space-x-3">
    <div name="left_container" class="relative flex h-full">
      <div name="row1" class="flex flex-col">
        {#each row1 as person (person.id)}
          <div class="border flex justify-center items-center h-6 w-14">
            <div class="text-center text-xs my-2"
            class:text-red-300="{person.gender === "女"}"
            class:text-blue-300="{person.gender === "男"}"
            >{person.name}</div>
          </div>
        {/each}
      </div>
      <div name="row2" class="flex flex-col">
        {#each row2 as person (person.id)}
          <div class="border flex justify-center items-center h-6 w-14">
            <div class="text-center text-xs my-2"
            class:text-red-300="{person.gender === "女"}"
            class:text-blue-300="{person.gender === "男"}"
            >{person.name}</div>
          </div>
        {/each}
      </div>

      <div class="absolute w-full bottom-0 ">
        <div class="border text-center ">門口</div>
      </div>
    </div>
    
    <div name="center_container"class="flex relative">
      <div name="row3" class="flex flex-col">
        {#each row3 as person (person.id)}
          <div class="border flex justify-center items-center h-6 w-14">
            <div class="text-center text-xs my-2"
            class:text-red-300="{person.gender === "女"}"
            class:text-blue-300="{person.gender === "男"}"
            >{person.name}</div>
          </div>
        {/each}
      </div>
      <div name="row4" class="flex flex-col">
        {#each row4 as person (person.id)}
          <div class="border flex justify-center items-center h-6 w-14">
            <div class="text-center text-xs my-2"
            class:text-red-300="{person.gender === "女"}"
            class:text-blue-300="{person.gender === "男"}"
            >{person.name}</div>
          </div>
        {/each}
      </div>
      <div name="row5" class="flex flex-col">
        {#each row5 as person (person.id)}
          <div class="border flex justify-center items-center h-6 w-14">
            <div class="text-center text-xs my-2"
            class:text-red-300="{person.gender === "女"}"
            class:text-blue-300="{person.gender === "男"}"
            >{person.name}</div>
          </div>
        {/each}
      </div>
      <div class="absolute w-full bottom-0 ">
        <div name="black_board" class="border text-center"
        on:mouseup={change_board}
        class:text-green-300="{clicked === true}">綠板</div>
      </div>
    </div>

    <div name="right_container" class="flex relative">
      <div name="row6" class="flex flex-col">
        {#each row6 as person (person.id)}
          <div class="border flex justify-center items-center h-6 w-14">
            <div class="text-center text-xs my-2"
            class:text-red-300="{person.gender === "女"}"
            class:text-blue-300="{person.gender === "男"}"
            >{person.name}</div>
          </div>
        {/each}
      </div>
      <div name="row7" class="flex flex-col">
        {#each row7 as person (person.id)}
          <div class="border flex justify-center items-center h-6 w-14">
            <div class="text-center text-xs my-2"
            class:text-red-300="{person.gender === "女"}"
            class:text-blue-300="{person.gender === "男"}"
            >{person.name}</div>
          </div>
        {/each}
      </div>
      <div class="absolute w-full bottom-0 ">
        <div class="border text-center">教壇</div>
      </div>
    </div>
  
  </div>
  <button on:click={shuffle} class="mx-auto border max-w-sm w-full font-serif hover:bg-white active:font-bold text-yellow-300">shuffle</button>
</main>

<style>

</style>
