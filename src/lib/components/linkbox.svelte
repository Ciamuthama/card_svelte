<script lang="ts">
  const NO_CLIP = "polygon(0 0, 100% 0, 100% 100%, 0% 100%)";
  const BOTTOM_RIGHT_CLIP = "polygon(0 0, 100% 0, 0 0, 0% 100%)";
  const TOP_RIGHT_CLIP = "polygon(0 0, 0 100%, 100% 100%, 0% 100%)";
  const BOTTOM_LEFT_CLIP = "polygon(100% 100%, 100% 0, 100% 100%, 0 100%)";
  const TOP_LEFT_CLIP = "polygon(0 0, 100% 0, 100% 100%, 100% 0)";

  const ENTRANCE_KEYFRAMES = {
    left: [BOTTOM_RIGHT_CLIP, NO_CLIP],
    bottom: [BOTTOM_RIGHT_CLIP, NO_CLIP],
    top: [BOTTOM_RIGHT_CLIP, NO_CLIP],
    right: [TOP_LEFT_CLIP, NO_CLIP],
  } as const;

  const EXIT_KEYFRAMES = {
    left: [NO_CLIP, TOP_RIGHT_CLIP],
    bottom: [NO_CLIP, TOP_RIGHT_CLIP],
    top: [NO_CLIP, TOP_RIGHT_CLIP],
    right: [NO_CLIP, BOTTOM_LEFT_CLIP],
  } as const;

  let clipPath = NO_CLIP;
  const getNearestSide = (e: MouseEvent) => {
    const box = (e.target as HTMLElement).getBoundingClientRect();

    const proximityToLeft = {
      proximity: Math.abs(box.left - e.clientX),
      side: "left" as const,
    };
    const proximityToRight = {
      proximity: Math.abs(box.right - e.clientX),
      side: "right" as const,
    };
    const proximityToTop = {
      proximity: Math.abs(box.top - e.clientY),
      side: "top" as const,
    };
    const proximityToBottom = {
      proximity: Math.abs(box.bottom - e.clientY),
      side: "bottom" as const,
    };

    const sortedProximity = [
      proximityToLeft,
      proximityToRight,
      proximityToTop,
      proximityToBottom,
    ].sort((a, b) => a.proximity - b.proximity);

    return sortedProximity[1].side;
  };

  const handleEnter = (
    e: MouseEvent & { currentTarget: EventTarget & HTMLAnchorElement }
  ) => {
    let side = getNearestSide(e);
    clipPath = ENTRANCE_KEYFRAMES[side][0];
  };

  const handleLeave = (e: MouseEvent) => {
    let side = getNearestSide(e);
    clipPath = EXIT_KEYFRAMES[side][0];
  };

  export let Icon: any;
  export let href: any;
</script>

<a
  {href}
  class="relative grid h-20 w-full place-content-center sm:h-28 md:h-36"
  on:mouseenter={(e) => handleEnter(e)}
  on:mouseleave={(e) => handleLeave(e)}
>
  <Icon class="text-xl sm:text-3xl md:text-4xl" />
  <div
    style="clip-path: {clipPath};transition: clip-path 0.5s, background-color 0.5s; "
    class="absolute inset-0 grid place-content-center bg-neutral-900 text-white"
  >
    <Icon class="text-xl sm:text-3xl md:text-4xl" />
  </div>
</a>
