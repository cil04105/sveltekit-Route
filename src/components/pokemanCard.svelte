<script>
	export let pokeman;
	// console.log(pokeman.id);
</script>

<a
	class="p-7 bg-gray-100 text-gray-800 text-center rounded-md shadow-sm hover:shadow-md flex flex-col items-center"
	href={`/pokemon/${pokeman.id}`}
>
	<img class="w-40 h-40" src={pokeman.image} alt={pokeman.name} />
	<h2 class="uppercase 2xl">{pokeman.id}. {pokeman.name}</h2>
</a>
