<script lang="ts">
  import TitleContent from "./lib/TitleContent/TitleContent.svelte";
  import TodoForm from "./lib/TodoContent/TodoForm.svelte";
  import TodoHeader from "./lib/TodoContent/TodoHeader.svelte";
  import TodoList from "./lib/TodoContent/TodoList.svelte";
</script>

<main
  class="w-full h-screen bg-[#EEE] flex flex-row justify-center items-center"
>
  <div class="max-w-[430px]">
    <TitleContent title="Todo" />
    <TodoHeader />
    <TodoForm />
  </div>
</main>
