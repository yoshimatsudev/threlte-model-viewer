<script>
	import { T, useFrame } from '@threlte/core';
	import { useGltf, OrbitControls, interactivity, Grid, useGltfAnimations } from '@threlte/extras';
	import { spring } from 'svelte/motion';
	import Chair from '$lib/components/Chair.svelte';
	import {
		AxesHelper,
		GridHelper,
		OrthographicCamera,
		PerspectiveCamera,
		AnimationLoader
	} from 'three';
	import Corkboard from './Corkboard.svelte';
	import LargeIsland from './Large_island.svelte';
	import Character from './Character.svelte';
	import { buttonIdle, buttonWalk, buttonRun } from '../character_state';
	import { Pane } from 'tweakpane';

	const pane = new Pane();

	const btn = pane.addButton({
		title: 'Run animation',
	});

	btn.on('click', () => {
		$buttonWalk = !$buttonWalk
	});

	let camera = { position: [0, 1, 0], zoom: 40 };
</script>

<T.OrthographicCamera makeDefault position={[1, 2, 0]} zoom={40}>
	<OrbitControls />
</T.OrthographicCamera>

<T.AmbientLight color="white" />

<!-- <Chair/> -->
<!-- <Corkboard scale={3}/> -->
<Character scale={1} position={[0, 1, 0]} />
<LargeIsland scale={1} position={[0, -0.39, 0]} />

<button style={'position: fixed'} on:click={() => $buttonIdle} />
