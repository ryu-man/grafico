<script>
  import { scaleStore } from '../scaleStore'
  import { scaleTime } from 'd3-scale'

  export let domain = [0, 1]
  export let range = [0, 1]
  export let rangeRound
  export let clamp = false
  export let interpolate
  export let nice
  export let unknown
  export let ticks
  export let tickFormat

  const scale = scaleStore(scaleTime())

  $: scale.domain(domain)
  $: scale.range(range)
  $: rangeRound && scale.get.rangeRound(rangeRound)
  $: scale.get.unknown(unknown)
  $: scale.get.clamp(clamp)
  $: interpolate && scale.get.interpolate(interpolate)
  $: scale.get.nice(nice)
</script>

<slot
  scale={$scale}
  domain={$scale.domain()}
  range={$scale.range()}
  ticks={$scale.ticks()}
  unknown={$scale.unknown()}
  interpolate={$scale.interpolate()}
  tickFormat={$scale.tickFormat(tickFormat)}
  invert={scale.get.invert}
  copy={scale.get.copy}
/>
