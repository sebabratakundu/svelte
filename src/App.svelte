<script>
	import Header from "./Header.svelte";
	import Modal from "./Modal.svelte";
	let name = "sebabrata";
	let job = "developer";
	let firstName = "nitish";
	let lastName = "kumar";
	let showModal = false;
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

	// array
	let students = [
		{
			id : 1,
			name : "ravi",
			roll : 23,
			marks : 80,
			subject : "Math"
		},
		{
			id : 2,
			name : "sanjib",
			roll : 4,
			marks : 60,
			subject : "Physics"
		},
		{
			id : 3,
			name : "Priti",
			roll : 7,
			marks : 93,
			subject : "Commerce"
		},
		{
			id : 4,
			name : "Ankush",
			roll : 43,
			marks : 55,
			subject : "History"
		},
		{
			id : 5,
			name : "Mitul",
			roll : 43,
			marks : 20,
			subject : "History"
		},
		{
			id : 6,
			name : "Gonesh",
			roll : 12,
			marks : 10,
			subject : "History"
		},
	];

	const deleteStudent = (id) => {
		students = students.filter(student => student.id != id);
	};

	const toggleModal = ()=>{
		showModal = !showModal;
	};
</script>

<!-- header component -->
<Header/>
<!-- modal component with props-->
<Modal title="Add Student" msg="Please register" {showModal} isPromo={true} on:click={toggleModal}>
	<div style="width: 100%;">
		<form>
			<input type="text" placeholder="name" class="form-control mb-4">
			<input type="number" placeholder="roll" class="form-control mb-4">
			<input type="number" placeholder="marks" class="form-control mb-4">
			<input type="text" placeholder="subject" class="form-control mb-4">
			<button>Submit</button>
		</form>
	</div>

	<!-- name slot -->
	<div slot="title">
		<!-- <h1>this is named slot</h1> -->
	</div>
</Modal>

<main>
	<h1>Hello {name}!</h1>
	<p>you are a {job}</p>
	<p>{fullName}</p>
	<!-- <input type="text" on:input={control} value={job}> -->
	
	<!-- two way binding -->
	<input type="text" bind:value={firstName}>
	<button on:click={changeValue}>Change</button>
	<br><br>

	<button on:click={toggleModal}>Open Modal</button>
	<br><br>
	<!-- loop -->
	{#each students as student (student.id)}
		<div class="stu-box">
			<h3>Name : {student.name}</h3>
			<p>Roll : {student.roll}</p>
			<p>Subject : {student.subject}</p>
			<p>Marks : {student.marks}</p>

			<!-- conditional logic -->
			{#if student.marks > 60}
				<p style="color: green;font-weight : 600">First Class</p>
			{:else if student.marks > 40 && student.marks <= 60}
				<p style="color: blue;font-weight : 600">Second Class</p>
			{:else if student.marks <= 20}
				<p style="color: red;font-weight : 600">Fail !</p>
			{/if}


			<!-- inline event handling -->
			<button style="background-color: red;color:white;" on:click={() => deleteStudent(student.id)}>Delete</button>
		</div>
	{:else}
		<p>No data found !</p>
	{/each}
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

	.stu-box{
		width: 100%;
		margin-bottom: 30px;		
		padding: 20px;
		box-shadow: 0 4px 10px #ddd;
	}
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>