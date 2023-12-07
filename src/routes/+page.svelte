<script lang="ts">
	let number = generateNumber();
	let score = 0;
	let message = '';

	console.log(number);

	function generateNumber() {
		const number = Math.floor(Math.random() * 100);
		if (number - 5 < 0) return generateNumber();
		return number;
	}

	function onSubmit(e) {
		const userNumber = e.target[0].value;
		score++;

		if (userNumber == number)
			return (
				(message = 'Wygrales!') &&
				setTimeout(() => {
					location.reload();
				}, 3000)
			);
		if (userNumber < number) return (message = 'Za mało');
		if (userNumber > number) return (message = 'Za duzo');
	}
</script>

<div class="container mx-auto">
	<header class="my-10 text-center">
		<h1 class="font-bold text-4xl">Zgadnij liczbę.</h1>
		<p class="my-1 font-semibold text-xl">
			Liczba z przedziału od {number - 5} do {number + 5}.
		</p>
		<p>
			Liczba prób <span class="font-semibold">{score}</span>.
		</p>
		<p class="font-bold text-lg">
			{message}
		</p>
	</header>

	<main class="flex justify-center text-center">
		<form on:submit={(e) => onSubmit(e)}>
			<input
				required
				min={0}
				type="number"
				class="border text-center mb-5 border-black rounded-md p-1 outline-none"
			/>
			<br />
			<button
				type="submit"
				class="text-sm bg-black rounded-lg px-10 py-3 uppercase text-white font-bold"
			>
				Zgadnij
			</button>
		</form>
	</main>
</div>
