<script lang="ts">
  export let todos: {
    id: string;
    date: string;
    title: string;
    completed: boolean;
  }[];
  export let handleDeleteTodo: (id: string) => void;

  const handleCheckCompleteTodo = (id: string) => {
    todos = todos.map((todo) =>
      todo.id === id ? { ...todo, completed: !todo.completed } : todo
    );
  };
</script>

<div class="font-inter bg-white px-7 pb-6">
  <ul class="flex flex-col w-full justify-between items-center gap-y-5">
    {#each todos as todo (todo.id)}
      <div class="flex flex-row w-full items-center justify-between">
        <div>
          <li class="text-[#0D0D0D] text-lg font-medium">
            <p class="whitespace-normal break-words max-w-[300px]">
              {todo.title}
            </p>
          </li>
          <span class="text-[#888] text-sm">{todo.date}</span>
        </div>
        <div class="flex flex-row gap-x-3">
          <!-- CheckBox -->
          <div
            class="cursor-pointer"
            on:click={() => handleCheckCompleteTodo(todo.id)}
            tabindex="0"
            role="button"
            on:keydown={(e) => {
              if (e.key === "Enter" || e.key === "Space") {
                () => handleCheckCompleteTodo(todo.id);
              }
            }}
          >
            {#if todo.completed === true}
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
            {:else}
              <svg
                xmlns="http://www.w3.org/2000/svg"
                width="24"
                height="24"
                viewBox="0 0 24 24"
                fill="none"
              >
                <path
                  d="M12 22C17.5228 22 22 17.5228 22 12C22 6.47715 17.5228 2 12 2C6.47715 2 2 6.47715 2 12C2 17.5228 6.47715 22 12 22Z"
                  stroke="#20EEB0"
                  stroke-width="2"
                />
              </svg>
            {/if}
          </div>
          <div
            on:click={() => handleDeleteTodo(todo.id)}
            class="cursor-pointer"
            tabindex="0"
            role="button"
            on:keydown={(e) => {
              if (e.key === "Enter" || e.key === "Space") {
                handleDeleteTodo(todo.id);
              }
            }}
          >
            <!-- RemoveIcon -->
            <svg
              xmlns="http://www.w3.org/2000/svg"
              width="24"
              height="24"
              viewBox="0 0 24 24"
              fill="none"
            >
              <path
                d="M2 6H22M10 11V16M14 11V16M4 6H20L18.42 20.22C18.3658 20.7094 18.1331 21.1616 17.7663 21.49C17.3994 21.8184 16.9244 22 16.432 22H7.568C7.07564 22 6.60056 21.8184 6.23375 21.49C5.86693 21.1616 5.63416 20.7094 5.58 20.22L4 6ZM7.345 3.147C7.50675 2.80397 7.76271 2.514 8.083 2.31091C8.4033 2.10782 8.77474 2 9.154 2H14.846C15.2254 1.99981 15.5971 2.10755 15.9176 2.31064C16.2381 2.51374 16.4942 2.80381 16.656 3.147L18 6H6L7.345 3.147V3.147Z"
                stroke="#FF4545"
                stroke-width="2"
                stroke-linecap="round"
                stroke-linejoin="round"
              />
            </svg>
          </div>
        </div>
      </div>
    {/each}
  </ul>
</div>
