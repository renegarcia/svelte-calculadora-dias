<script>
	let elapsedDays = '';
	let initDate = null;
	let endDate = null;

	function computeDays() {
		let init = new Date(initDate);
		let end = new Date(endDate);
		elapsedDays = Math.floor((end - init) / 1000 / 3600 / 24) + 1;
	}
</script>

<h1>Calculadora de días</h1>
<p>
	<strong>Instrucciones:</strong> Selecciona los días inicial y final para ver el número de días transcurridos.
</p>
<div>
	<form on:submit|preventDefault={computeDays}>
		<label for="inicioInput">Inicio</label>
		<input type="date" id="inicioInput" bind:value={initDate} required>
		<label  for="finInput">Fin</label>
		<input type="date" bind:value={endDate} id="finInput" required>
		<input type="submit" value="Calcular">
	</form>
</div>
<div>
	<p>
		Días transcurridos: {elapsedDays || "-" }
	</p>
</div>
