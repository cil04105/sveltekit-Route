<!-- [id].svelte 는 이페이지를 어떤 용도로 사욜할 것 이라는 것이다, url에서 해당 세부 정보 가져오기 -->
<script context="module">
	export async function load({ params }) {
		//최신 버전에서는 page>params

		const id = params.id;
		const url = `https://pokeapi.co/api/v2/pokemon/${id}`;
		const res = await fetch(url);
		const pokeman = await res.json();

		return { props: { pokeman } };
	}
</script>

<script>
	export let pokeman;
	const type = pokeman.types[0].type.name;
</script>

<div class="flex flex-col items center">
	<h1 class="text-4xl text-center my-8 uppercase">{pokeman.name}</h1>
	<p>
		Type: <strong>{type}</strong> | Height: <strong>{pokeman.height}</strong> | Weight:
		<strong>{pokeman.weight}</strong>
	</p>
	<img class="card-image" src={pokeman.sprites['front_default']} alt={pokeman.name} />
</div>
