<script lang="ts">
  export let todos: {
    id: string;
    date: string;
    title: string;
    completed: boolean;
  }[];
  export let handleDeleteTodo: (id: string) => void;
</script>

<div class="font-inter bg-white px-7 pb-6">
  <ul class="flex flex-col w-full justify-between items-center gap-y-5">
    {#each todos as todo (todo.id)}
      <div class="flex flex-row w-full items-center justify-between">
        <div>
          <li class="text-[#0D0D0D] text-lg font-medium">{todo.title}</li>
          <span class="text-[#888] text-sm">{todo.date}</span>
        </div>
        <div class="flex flex-row gap-x-3">
          <!-- CheckBox -->
          <div class="cursor-pointer">
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
