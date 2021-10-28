<script>
	let name = "sebabrata";
	let job = "developer";
	let firstName = "nitish";
	let lastName = "kumar";
	// funciton
	// const control = (e)=>{
	// 	firstName = (e.target.value);
	// };

	const changeValue = () =>{
		job = "Manager";
	};

	// reative value
	$: fullName = `${firstName} - ${lastName}`;

	// reative statement
	// $: console.log(firstName);

	// reactive multiple statements
	$: {
		console.log(firstName);
		console.log(lastName);
	}
</script>

<main>
	<h1>Hello {name}!</h1>
	<p>you are a {job}</p>
	<p>{fullName}</p>
	<!-- <input type="text" on:input={control} value={job}> -->
	
	<!-- two way binding -->
	<input type="text" bind:value={firstName}>
	<button on:click={changeValue}>Change</button>
</main>

<style>
	button{
		background:purple;
		color : white;
		border : none;
		padding : 8px 15px;
	}

	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>