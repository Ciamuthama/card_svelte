<script lang="ts">
    import Card from "$lib/components/card.svelte";
import Clip from "$lib/components/clipathlinks.svelte";
</script>

<div class="bg-white">
  <div class="bg-[#6797ff4a] px-4 py-12">
  <iframe src="/clippath" title="clippath" frameborder="0" class="mx-auto max-w-7xl mb-10 w-full h-[33rem]">
    <Clip />
  </iframe>
  <iframe src="/card" title="card" frameborder="0" class="mx-auto max-w-7xl mb-10 w-full h-[33rem]">
    <Card />
  </iframe>
</div>
</div>