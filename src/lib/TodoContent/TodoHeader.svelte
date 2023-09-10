<script lang="ts">
  import TodoHeaderImage from "../../assets/TodoHeaderImage.jpg";
  import { onMount, onDestroy } from "svelte";

  let currentDate: Date = new Date();

  function updateCurrentDate() {
    currentDate = new Date();
  }

  let interval: number;

  onMount(() => {
    updateCurrentDate();
    interval = setInterval(updateCurrentDate, 1000);
  });

  onDestroy(() => {
    clearInterval(interval);
  });

  function formatDateTime(date: Date): { dateStr: string; timeStr: string } {
    const options: Intl.DateTimeFormatOptions = {
      weekday: "short",
      day: "numeric",
    };
    const dateStr: string = date.toLocaleDateString(undefined, options);
    const timeStr: string = date.toLocaleTimeString(undefined, {
      hour: "numeric",
      minute: "numeric",
      hour12: true,
    });
    return { dateStr, timeStr };
  }
</script>

<div class="relative">
  <img
    src={TodoHeaderImage}
    alt="TodoHeaderImage"
    class="w-[430px] h-[202px] rounded-t-[10px]"
  />
  <div class="absolute flex flex-col font-russoOne text-white right-7 bottom-3">
    <span class="text-lg text-right">{formatDateTime(currentDate).dateStr}</span
    >
    <h1 class="text-5xl">{formatDateTime(currentDate).timeStr}</h1>
  </div>
</div>
