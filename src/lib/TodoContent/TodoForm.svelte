<script lang="ts">
  import { v4 as uuidv4 } from "uuid";
  import TodoList from "./TodoList.svelte";
  let date = new Date();
  let inputText: string = "";
  let todos: { id: string; date: string; title: string; completed: boolean }[] =
    [];

  const formatDateTime = (date: Date): string => {
    const options: Intl.DateTimeFormatOptions = {
      hour: "numeric",
      minute: "numeric",
      hour12: true,
    };
    return date.toLocaleTimeString(undefined, options);
  };

  const handleAddTodo = () => {
    if (inputText != "") {
      const currentDate = new Date();
      todos = [
        ...todos,
        {
          id: uuidv4(),
          title: inputText,
          date: `Today at ${formatDateTime(currentDate)}`,
          completed: false,
        },
      ];
      inputText = "";
    } else {
      return;
    }
  };

  const handleDeleteTodo = (id: string) => {
    todos = todos.filter((todo) => todo.id !== id);
  };
</script>

<form on:submit|preventDefault={handleAddTodo}>
  <div class="bg-white pt-6 pb-9 px-7 flex flex-row justify-between">
    <div class="relative">
      <input
        bind:value={inputText}
        type="text"
        placeholder="Note"
        class="w-[275px] bg-[#EBEFF2] py-3 pl-10 focus:outline-none"
      />
      <div class="absolute top-3 left-2">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="24"
          height="24"
          viewBox="0 0 24 24"
          fill="none"
        >
          <path
            d="M12 22C17.5228 22 22 17.5228 22 12C22 6.47715 17.5228 2 12 2C6.47715 2 2 6.47715 2 12C2 17.5228 6.47715 22 12 22Z"
            fill="#20EEB0"
            stroke="#20EEB0"
            stroke-width="2"
          />
          <path
            d="M10.7783 14.657L8.9143 12.7253C8.81386 12.6212 8.67763 12.5628 8.53558 12.5628C8.39354 12.5628 8.25731 12.6212 8.15687 12.7253C8.05643 12.8294 8 12.9706 8 13.1178C8 13.1907 8.01385 13.2628 8.04077 13.3302C8.06768 13.3975 8.10714 13.4587 8.15687 13.5102L10.4023 15.8372C10.6118 16.0543 10.9502 16.0543 11.1597 15.8372L16.8431 9.94748C16.9436 9.8434 17 9.70222 17 9.55502C17 9.40782 16.9436 9.26665 16.8431 9.16256C16.7427 9.05848 16.6065 9 16.4644 9C16.3224 9 16.1861 9.05848 16.0857 9.16256L10.7783 14.657Z"
            fill="white"
          />
        </svg>
      </div>
    </div>
    <button
      type="submit"
      class="bg-[#20EEB0] w-[88px] flex items-center justify-center"
    >
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="18"
        height="19"
        viewBox="0 0 18 19"
        fill="none"
      >
        <path
          d="M9 17.5V9.5M9 9.5V1.5M9 9.5H17M9 9.5H1"
          stroke="white"
          stroke-width="2"
          stroke-linecap="round"
        />
      </svg>
    </button>
  </div>
</form>

<TodoList bind:todos {handleDeleteTodo} />
