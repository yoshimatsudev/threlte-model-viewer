<!--
Auto-generated by: https://github.com/threlte/threlte/tree/main/packages/gltf
Command: npx @threlte/gltf@1.0.1 static/models/tree.glb
-->

<script>
  import { Group } from 'three'
  import { T, forwardEventHandlers } from '@threlte/core'
  import { useGltf } from '@threlte/extras'

  export const ref = new Group()

  const gltf = useGltf('models/tree.glb')

  const component = forwardEventHandlers()
</script>

<T is={ref} dispose={false} {...$$restProps} bind:this={$component}>
  {#await gltf}
    <slot name="fallback" />
  {:then gltf}
    <T.Mesh geometry={gltf.nodes['Tree_Cylinder-Mesh'].geometry} material={gltf.materials.Wood} />
    <T.Mesh geometry={gltf.nodes['Tree_Cylinder-Mesh_1'].geometry} material={gltf.materials.Leaves} />
  {:catch error}
    <slot name="error" {error} />
  {/await}

  <slot {ref} />
</T>
