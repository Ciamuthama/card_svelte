<script>
  import Linkbox from "$lib/components/linkbox.svelte";
  import { Apple, Figma, Facebook, Framer ,Gem, Linkedin,Send,Twitter ,Youtube  } from 'lucide-svelte';
</script>

<div class="divide-y divide-neutral-900 border border-neutral-900">
  <div class="grid grid-cols-2 w-full divide-x divide-neutral-900">
    <Linkbox Icon={Apple} href=""/>
    <Linkbox Icon={Figma} href=""/>
  </div>
  <div class="grid grid-cols-4 w-full divide-x divide-neutral-900">
    <Linkbox Icon={Facebook} href=""/>
    <Linkbox Icon={Framer} href=""/>
    <Linkbox Icon={Gem } href=""/>
    <Linkbox Icon={Linkedin} href=""/>
  </div>
  <div class="grid grid-cols-3 w-full divide-x divide-neutral-900">
    <Linkbox Icon={Send } href=""/>
    <Linkbox Icon={Twitter } href=""/>
    <Linkbox Icon={Youtube} href=""/>
  </div>
</div>
